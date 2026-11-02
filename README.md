// ==========================================
// 1. FUNCIÓN PARA CREAR LA HOJA DE CÁLCULO
// ==========================================
function crearHojaYConfigurar() {
  const ss = SpreadsheetApp.create('Base de Datos - Accidentes de Trabajo');
  const sheet = ss.getActiveSheet();
  sheet.setName('Accidentes');
  
  const headers = [
    'Timestamp', 'NumRegistro', 
    'RazonSocial', 'RUC', 'Domicilio', 'ActividadEconomica', 'NumTrabajadores',
    'SCTR_Afiliados', 'SCTR_NoAfiliados', 'Aseguradora',
    'Contratista_RazonSocial', 'Contratista_RUC', 'Contratista_Domicilio', 'Contratista_Actividad', 'Contratista_NumTrabajadores',
    'Contratista_SCTR_Afiliados', 'Contratista_SCTR_NoAfiliados', 'Contratista_Aseguradora',
    'ApellidosNombres', 'DNI', 'Edad', 'Area', 'Puesto', 'Antiguedad', 'Sexo', 'Turno', 'TipoContrato', 'Experiencia', 'HorasTrabajadas',
    'FechaAccidente', 'HoraAccidente', 'FechaInvestigacion', 'LugarExacto', 'Gravedad', 
    'TotalTemporal', 'ParcialTemporal', 'ParcialPermanente', 'TotalPermanente',
    'DiasDescanso', 'TrabajadoresAfectados', 'ParteCuerpo', 'Descripcion', 'Causas',
    'Medida1_Desc', 'Medida1_Resp', 'Medida1_Fecha', 'Medida1_Estado',
    'Medida2_Desc', 'Medida2_Resp', 'Medida2_Fecha', 'Medida2_Estado',
    'Responsable1_Nombre', 'Responsable1_Cargo', 'Responsable1_Fecha',
    'Responsable2_Nombre', 'Responsable2_Cargo', 'Responsable2_Fecha'
  ];

  sheet.getRange(1, 1, 1, headers.length).setValues([headers]);
  const headerRange = sheet.getRange(1, 1, 1, headers.length);
  headerRange.setFontWeight('bold');
  headerRange.setBackground('#1e293b'); // Color oscuro elegante
  headerRange.setFontColor('#ffffff');
  headerRange.setHorizontalAlignment('center');
  sheet.setFrozenRows(1);
  
  for (let i = 1; i <= headers.length; i++) { sheet.autoResizeColumn(i); }
  
  PropertiesService.getScriptProperties().setProperty('SPREADSHEET_ID', ss.getId());
  Logger.log('✅ HOJA CREADA. URL: ' + ss.getUrl());
}

// ==========================================
// 2. RECIBIR DATOS (GUARDAR / EDITAR / ELIMINAR)
// ==========================================
function doPost(e) {
  try {
    const spreadsheetId = PropertiesService.getScriptProperties().getProperty('SPREADSHEET_ID');
    if (!spreadsheetId) throw new Error("Ejecuta crearHojaYConfigurar() primero.");
    
    const sheet = SpreadsheetApp.openById(spreadsheetId).getActiveSheet();
    const data = e.parameter;
    
    // --- ELIMINAR ---
    if (data.action === 'delete') {
      const numReg = data.NumRegistro;
      const lastRow = sheet.getLastRow();
      if (lastRow > 1) {
        const regValues = sheet.getRange(2, 2, lastRow - 1, 1).getValues().flat();
        const foundIndex = regValues.indexOf(numReg.toString());
        if (foundIndex !== -1) {
          sheet.deleteRow(foundIndex + 2);
          return ContentService.createTextOutput(JSON.stringify({ result: 'deleted' })).setMimeType(ContentService.MimeType.JSON);
        }
      }
      return ContentService.createTextOutput(JSON.stringify({ result: 'not_found' })).setMimeType(ContentService.MimeType.JSON);
    }

    // --- GUARDAR / EDITAR ---
    let headers = sheet.getRange(1, 1, 1, sheet.getLastColumn()).getValues()[0];
    const numRegistro = data['NumRegistro'];
    let rowToUpdate = -1;

    if (numRegistro && sheet.getLastRow() > 1) {
      const regValues = sheet.getRange(2, 2, sheet.getLastRow() - 1, 1).getValues().flat();
      const foundIndex = regValues.indexOf(numRegistro.toString());
      if (foundIndex !== -1) rowToUpdate = foundIndex + 2; 
    }

    const newRow = headers.map(header => {
      if (header === 'Timestamp') {
         return rowToUpdate !== -1 ? sheet.getRange(rowToUpdate, 1).getValue() : new Date();
      }
      return data[header] || '';
    });

    if (rowToUpdate !== -1) {
      sheet.getRange(rowToUpdate, 1, 1, headers.length).setValues([newRow]);
      return ContentService.createTextOutput(JSON.stringify({ result: 'updated' })).setMimeType(ContentService.MimeType.JSON);
    } else {
      sheet.appendRow(newRow);
      return ContentService.createTextOutput(JSON.stringify({ result: 'created' })).setMimeType(ContentService.MimeType.JSON);
    }
  } catch (error) {
    return ContentService.createTextOutput(JSON.stringify({ result: 'error', error: error.toString() })).setMimeType(ContentService.MimeType.JSON);
  }
}

// ==========================================
// 3. ENVIAR DATOS AL HTML (HISTORIAL)
// ==========================================
function doGet(e) {
  if (e && e.parameter && e.parameter.action === 'getData') {
    return obtenerDatos();
  }
  return ContentService.createTextOutput("API funcionando correctamente.");
}

function obtenerDatos() {
  const spreadsheetId = PropertiesService.getScriptProperties().getProperty('SPREADSHEET_ID');
  if (!spreadsheetId) return ContentService.createTextOutput(JSON.stringify([])).setMimeType(ContentService.MimeType.JSON);
  
  const sheet = SpreadsheetApp.openById(spreadsheetId).getActiveSheet();
  const lastRow = sheet.getLastRow();
  if (lastRow <= 1) return ContentService.createTextOutput(JSON.stringify([])).setMimeType(ContentService.MimeType.JSON);
  
  const headers = sheet.getRange(1, 1, 1, sheet.getLastColumn()).getValues()[0];
  const data = sheet.getRange(2, 1, lastRow - 1, headers.length).getValues();
  
  let result = [];
  for (let i = 0; i < data.length; i++) {
    let rowObj = {};
    for (let j = 0; j < headers.length; j++) {
      let val = data[i][j];
      if (val instanceof Date) {
        val = Utilities.formatDate(val, Session.getScriptTimeZone(), "yyyy-MM-dd");
      }
      rowObj[headers[j]] = val;
    }
    result.push(rowObj);
  }
  return ContentService.createTextOutput(JSON.stringify(result)).setMimeType(ContentService.MimeType.JSON);
}

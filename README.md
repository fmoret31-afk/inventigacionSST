<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Registro de Accidentes - RM 050-2013-TR</title>
    
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700&display=swap" rel="stylesheet">
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    
    <style>
        :root {
            --primary: #2563eb;
            --success: #10b981;
            --danger: #ef4444;
            --info: #0ea5e9;
            --dark: #1e293b;
            --gray: #64748b;
            --bg-body: #f1f5f9;
            --border-color: #94a3b8;
            --input-bg: #f8fafc;
        }

        body { 
            font-family: 'Inter', sans-serif; 
            font-size: 11px; 
            margin: 0; 
            padding: 20px; 
            background-color: var(--bg-body); 
            color: var(--dark); 
            -webkit-font-smoothing: antialiased;
        }
        
        .container { 
            width: 100%; 
            max-width: 1300px; 
            margin: 0 auto; 
            background-color: #fff; 
            padding: 25px; 
            box-shadow: 0 10px 25px -5px rgba(0, 0, 0, 0.1); 
            border-radius: 12px;
        }
        
        /* TABLAS */
        .excel-table { 
            width: 100%; 
            border-collapse: collapse; 
            margin-bottom: -1px; 
            table-layout: fixed; 
            border: 1px solid var(--border-color); 
        }
        .excel-table th, .excel-table td { 
            border: 1px solid var(--border-color); 
            padding: 4px; 
            vertical-align: middle; 
            text-align: center; 
            word-wrap: break-word;
        }
        
        /* CABECERAS */
        .excel-table th { background-color: #e2e8f0; font-weight: 700; font-size: 9px; text-transform: uppercase; color: #334155; letter-spacing: 0.3px;}
        .section-title { background-color: var(--dark) !important; color: #fff !important; font-weight: 600; text-align: left !important; font-size: 10px; padding: 6px 10px !important; letter-spacing: 0.5px;}
        .sub-section { background-color: #f1f5f9 !important; font-size: 8px; font-weight: 600; text-align: left !important; padding: 4px 10px !important; color: var(--gray); }
        
        /* CAJONES DE TEXTO */
        input[type="text"], input[type="date"], input[type="time"], input[type="number"], textarea, select {
            width: 100%; 
            border: 1px solid transparent; 
            background: var(--input-bg); 
            font-family: 'Inter', sans-serif; 
            font-size: 11px; 
            font-weight: 500; 
            box-sizing: border-box; 
            text-align: center; 
            padding: 4px; 
            border-radius: 4px;
            color: var(--dark);
            transition: all 0.2s ease;
            display: block;
        }

        input:focus, textarea:focus, select:focus { 
            outline: none; 
            border-color: var(--primary); 
            background-color: #fff; 
            box-shadow: 0 0 0 2px rgba(37, 99, 235, 0.15); 
        }

        textarea { 
            text-align: left; 
            resize: vertical; 
            min-height: 70px; 
            line-height: 1.4; 
            font-weight: 400;
            width: 100% !important;
            border: 1px solid var(--border-color);
        }
        
        .input-left { text-align: left !important; padding-left: 6px;}
        .concepto { font-size: 8px; color: var(--gray); font-style: italic; display: block; margin-top: 3px; text-align: left; font-weight: 400;}

        /* 🔥 NUEVA CLASE PARA HACER MÁS PEQUEÑOS LOS CHECKBOX Y TEXTOS 🔥 */
        .label-checkbox {
            display: inline-flex;
            align-items: center;
            font-size: 9px; /* Letra más pequeña */
            font-weight: 600;
            color: #334155;
            margin-right: 8px;
            margin-bottom: 2px;
            cursor: pointer;
            white-space: nowrap;
        }
        .label-checkbox input {
            width: 12px;
            height: 12px;
            margin: 0 4px 0 0; /* Espacio entre el cuadro y el texto */
            cursor: pointer;
        }

        /* BOTONES */
        .btn-container { display: flex; justify-content: center; flex-wrap: wrap; gap: 12px; margin: 25px 0; }
        .btn { 
            display: inline-flex; align-items: center; justify-content: center; gap: 6px;
            padding: 10px 20px; font-size: 13px; font-weight: 600; cursor: pointer; 
            border: none; border-radius: 6px; color: white; transition: all 0.3s ease;
            box-shadow: 0 2px 4px rgba(0,0,0,0.1); font-family: 'Inter', sans-serif;
        }
        .btn i { font-size: 14px; }
        .btn:hover { transform: translateY(-2px); box-shadow: 0 4px 8px rgba(0,0,0,0.15); filter: brightness(1.05); }
        .btn-save { background-color: var(--success); }
        .btn-print { background-color: var(--primary); }
        .btn-clear { background-color: var(--danger); }
        .btn-update { background-color: var(--info); }

        /* HISTORIAL */
        .admin-section { margin-top: 40px; }
        .card { background: #ffffff; border-radius: 10px; box-shadow: 0 4px 6px -1px rgba(0, 0, 0, 0.05); overflow: hidden; border: 1px solid var(--border-color); }
        .card-header { background-color: #f8fafc; padding: 15px 20px; border-bottom: 1px solid var(--border-color); display: flex; justify-content: space-between; align-items: center; }
        .card-title { margin: 0; font-size: 16px; font-weight: 700; color: var(--dark); display: flex; align-items: center; gap: 8px; }
        .card-title i { color: var(--primary); }
        .table-responsive { overflow-x: auto; padding: 15px 20px; }
        .admin-table { width: 100%; border-collapse: collapse; font-size: 12px; }
        .admin-table th, .admin-table td { padding: 10px; text-align: left; border-bottom: 1px solid var(--border-color); }
        .admin-table th { background-color: #f1f5f9; color: #475569; font-weight: 600; text-transform: uppercase; font-size: 10px; }
        .admin-table tbody tr:hover { background-color: #f8fafc; }
        .action-btns { display: flex; gap: 6px; justify-content: center; }
        .btn-action { display: inline-flex; align-items: center; gap: 4px; padding: 6px 12px; font-size: 11px; font-weight: 600; border: none; border-radius: 4px; cursor: pointer; transition: 0.2s; }
        .btn-edit { background-color: #fef3c7; color: #b45309; }
        .btn-del { background-color: #fee2e2; color: #b91c1c; }
        .empty-msg { text-align: center; color: var(--gray); font-style: italic; padding: 20px; }

        /* IMPRESIÓN A4 */
        @media print {
            @page { size: A4 portrait; margin: 8mm; }
            body { background-color: #fff; padding: 0; margin: 0; font-size: 10px; }
            .container { box-shadow: none; padding: 0; max-width: 100%; width: 100%; border: none; }
            .btn-container, .admin-section, .concepto { display: none !important; }
            .excel-table { page-break-inside: avoid; width: 100% !important; margin-bottom: 2px;}
            textarea { border: 1px solid #000 !important; background: transparent !important; min-height: 80px !important; page-break-inside: avoid; }
            input, select { border: none !important; background: transparent !important; }
            .section-title { background-color: #e2e8f0 !important; color: #000 !important; border: 1px solid #000; -webkit-print-color-adjust: exact; }
            .excel-table th { background-color: #f1f5f9 !important; color: #000 !important; border: 1px solid #000; -webkit-print-color-adjust: exact; }
            .label-checkbox { color: #000; font-size: 8.5px;}
        }
    </style>
</head>
<body>

<div class="container">
    <form id="formAccidente">
        
        <!-- ENCABEZADO -->
        <table class="excel-table" style="border: none;">
            <tr>
                <td style="text-align: left; font-weight: 700; border: none; width: 30%; font-size: 12px;">
                    Nº REGISTRO: <input type="text" name="NumRegistro" id="NumRegistro" style="width: 100px; text-align: center; font-weight: 700; color: var(--primary); border-color: var(--border-color); display:inline-block;">
                </td>
                <td colspan="9" style="border: none; text-align: center;">
                    <h2 style="margin: 0; font-size: 18px; font-weight: 700; text-transform: uppercase;">REGISTRO DE ACCIDENTES DE TRABAJO</h2>
                    <span style="font-size: 10px; color: var(--gray);">Formato RM 050-2013-TR</span>
                </td>
                <td style="border: none; width: 30%;"></td>
            </tr>
        </table>

        <!-- 1. DATOS DEL EMPLEADOR -->
        <table class="excel-table">
            <tr><td colspan="12" class="section-title">DATOS DEL EMPLEADOR PRINCIPAL</td></tr>
            <tr>
                <th colspan="4">RAZÓN SOCIAL O DENOMINACIÓN</th>
                <th colspan="2">RUC</th>
                <th colspan="3">DOMICILIO</th>
                <th colspan="2">ACTIVIDAD ECONÓMICA</th>
                <th colspan="1">Nº TRABAJADORES</th>
            </tr>
            <tr>
                <td colspan="4"><input type="text" name="RazonSocial" class="input-left"></td>
                <td colspan="2"><input type="text" name="RUC"></td>
                <td colspan="3"><input type="text" name="Domicilio" class="input-left"></td>
                <td colspan="2"><input type="text" name="ActividadEconomica" class="input-left"></td>
                <td colspan="1">
                    <input type="number" name="NumTrabajadores">
                    <span class="concepto">Total en la sede</span>
                </td>
            </tr>
            <tr><td colspan="12" class="sub-section">COMPLETAR SÓLO EN CASO DE ALTO RIESGO</td></tr>
            <tr>
                <th colspan="4">AFILIADOS AL SCTR</th>
                <th colspan="4">NO AFILIADOS AL SCTR</th>
                <th colspan="4">ASEGURADORA</th>
            </tr>
            <tr>
                <td colspan="4"><input type="number" name="SCTR_Afiliados"></td>
                <td colspan="4"><input type="number" name="SCTR_NoAfiliados"></td>
                <td colspan="4"><input type="text" name="Aseguradora" placeholder="Ej. PACIFICO"></td>
            </tr>
        </table>

        <!-- 2. EMPLEADOR DE INTERMEDIACIÓN -->
        <table class="excel-table">
            <tr><td colspan="12" class="section-title">DATOS DEL EMPLEADOR DE INTERMEDIACIÓN / CONTRATISTA</td></tr>
            <tr>
                <th colspan="4">RAZÓN SOCIAL</th>
                <th colspan="2">RUC</th>
                <th colspan="3">DOMICILIO</th>
                <th colspan="2">ACTIVIDAD ECONÓMICA</th>
                <th colspan="1">Nº TRABAJADORES</th>
            </tr>
            <tr>
                <td colspan="4"><input type="text" name="Contratista_RazonSocial" class="input-left"></td>
                <td colspan="2"><input type="text" name="Contratista_RUC"></td>
                <td colspan="3"><input type="text" name="Contratista_Domicilio" class="input-left"></td>
                <td colspan="2"><input type="text" name="Contratista_Actividad" class="input-left"></td>
                <td colspan="1"><input type="number" name="Contratista_NumTrabajadores"></td>
            </tr>
            <tr><td colspan="12" class="sub-section">COMPLETAR SÓLO EN CASO DE ALTO RIESGO</td></tr>
            <tr>
                <th colspan="4">AFILIADOS AL SCTR</th>
                <th colspan="4">NO AFILIADOS AL SCTR</th>
                <th colspan="4">ASEGURADORA</th>
            </tr>
            <tr>
                <td colspan="4"><input type="number" name="Contratista_SCTR_Afiliados"></td>
                <td colspan="4"><input type="number" name="Contratista_SCTR_NoAfiliados"></td>
                <td colspan="4"><input type="text" name="Contratista_Aseguradora"></td>
            </tr>
        </table>

        <!-- 3. DATOS DEL TRABAJADOR -->
        <table class="excel-table">
            <tr><td colspan="12" class="section-title">DATOS DEL TRABAJADOR ACCIDENTADO</td></tr>
            <tr>
                <th colspan="6">APELLIDOS Y NOMBRES</th>
                <th colspan="3">DNI / CE</th>
                <th colspan="3">EDAD</th>
            </tr>
            <tr>
                <td colspan="6"><input type="text" name="ApellidosNombres" class="input-left"></td>
                <td colspan="3"><input type="text" name="DNI"></td>
                <td colspan="3"><input type="number" name="Edad"></td>
            </tr>
            <tr>
                <th colspan="2">ÁREA</th>
                <th colspan="2">PUESTO</th>
                <th colspan="2">ANTIGÜEDAD</th>
                <th>SEXO (F/M)</th>
                <th>TURNO (D/T/N)</th>
                <th colspan="2">CONTRATO</th>
                <th colspan="2">EXPERIENCIA</th>
            </tr>
            <tr>
                <td colspan="2"><input type="text" name="Area"></td>
                <td colspan="2"><input type="text" name="Puesto"></td>
                <td colspan="2"><input type="text" name="Antiguedad"></td>
                <td><input type="text" name="Sexo" maxlength="1"></td>
                <td><input type="text" name="Turno" maxlength="1"></td>
                <td colspan="2"><input type="text" name="TipoContrato"></td>
                <td colspan="2"><input type="text" name="Experiencia"></td>
            </tr>
            <tr>
                <th colspan="12">HORAS TRABAJADAS EN LA JORNADA (Antes del accidente)</th>
            </tr>
            <tr>
                <td colspan="12"><input type="number" name="HorasTrabajadas"></td>
            </tr>
        </table>

        <!-- 4. INVESTIGACIÓN (AQUÍ ESTÁ LA CORRECCIÓN DE LAS LETRAS) -->
        <table class="excel-table">
            <tr><td colspan="12" class="section-title">INVESTIGACIÓN DEL ACCIDENTE DE TRABAJO</td></tr>
            <tr>
                <th colspan="4">FECHA Y HORA DEL ACCIDENTE</th>
                <th colspan="4">INICIO DE LA INVESTIGACIÓN</th>
                <th colspan="4">LUGAR EXACTO</th>
            </tr>
            <tr>
                <td colspan="4">
                    <input type="date" name="FechaAccidente" style="width: 55%; display:inline-block;"> 
                    <input type="time" name="HoraAccidente" style="width: 40%; display:inline-block;">
                </td>
                <td colspan="4"><input type="date" name="FechaInvestigacion"></td>
                <td colspan="4"><input type="text" name="LugarExacto" class="input-left"></td>
            </tr>
            <tr>
                <th colspan="4">GRAVEDAD DEL ACCIDENTE</th>
                <th colspan="4">GRADO INCAPACITANTE</th>
                <th colspan="2">DÍAS DESCANSO</th>
                <th colspan="2">TRABAJADORES AFECTADOS</th>
            </tr>
            <tr>
                <!-- SE APLICÓ LA CLASE label-checkbox PARA REDUCIR EL TAMAÑO -->
                <td colspan="4" style="text-align: left; padding-left: 8px;">
                    <label class="label-checkbox"><input type="radio" name="Gravedad" value="Leve"> LEVE</label>
                    <label class="label-checkbox"><input type="radio" name="Gravedad" value="Incapacitante"> INCAPACITANTE</label>
                    <label class="label-checkbox"><input type="radio" name="Gravedad" value="Mortal"> MORTAL</label>
                </td>
                <td colspan="4" style="text-align: left; padding-left: 8px;">
                    <label class="label-checkbox"><input type="checkbox" name="TotalTemporal" value="Sí"> TOTAL TEMPORAL</label>
                    <label class="label-checkbox"><input type="checkbox" name="ParcialTemporal" value="Sí"> PARCIAL TEMPORAL</label>
                    <label class="label-checkbox"><input type="checkbox" name="ParcialPermanente" value="Sí"> PARCIAL PERMANENTE</label>
                    <label class="label-checkbox"><input type="checkbox" name="TotalPermanente" value="Sí"> TOTAL PERMANENTE</label>
                </td>
                <td colspan="2"><input type="number" name="DiasDescanso"></td>
                <td colspan="2"><input type="number" name="TrabajadoresAfectados"></td>
            </tr>
            <tr>
                <th colspan="12">PARTE DEL CUERPO LESIONADO</th>
            </tr>
            <tr>
                <td colspan="12"><input type="text" name="ParteCuerpo" class="input-left"></td>
            </tr>
        </table>

        <!-- 5. DESCRIPCIÓN -->
        <table class="excel-table">
            <tr><td colspan="12" class="section-title">DESCRIPCIÓN DEL ACCIDENTE</td></tr>
            <tr>
                <td colspan="12" style="text-align: left; padding: 10px;">
                    <span class="concepto" style="margin-bottom: 5px; font-size: 9px;"><i class="fas fa-info-circle"></i> Describa sólo los hechos comprobables. Adjuntar declaraciones y procedimientos.</span>
                    <textarea name="Descripcion" placeholder="Escriba aquí el relato cronológico del accidente..."></textarea>
                </td>
            </tr>
        </table>

        <!-- 6. CAUSAS -->
        <table class="excel-table">
            <tr><td colspan="12" class="section-title">CAUSAS QUE ORIGINARON EL ACCIDENTE</td></tr>
            <tr>
                <td colspan="12" style="text-align: left; padding: 10px;">
                    <span class="concepto" style="margin-bottom: 5px; font-size: 9px;"><i class="fas fa-info-circle"></i> Use el modelo de causalidad (Inmediatas, Básicas, Fallas de Control).</span>
                    <textarea name="Causas" placeholder="Desarrolle el análisis de causas aquí..."></textarea>
                </td>
            </tr>
        </table>

        <!-- 7. MEDIDAS CORRECTIVAS -->
        <table class="excel-table">
            <tr><td colspan="12" class="section-title">MEDIDAS CORRECTIVAS</td></tr>
            <tr>
                <th colspan="4">DESCRIPCIÓN DE LA MEDIDA</th>
                <th colspan="3">RESPONSABLE</th>
                <th colspan="3">FECHA EJECUCIÓN</th>
                <th colspan="2">ESTADO</th>
            </tr>
            <tr>
                <td colspan="4"><input type="text" name="Medida1_Desc" class="input-left"></td>
                <td colspan="3"><input type="text" name="Medida1_Resp"></td>
                <td colspan="3"><input type="date" name="Medida1_Fecha"></td>
                <td colspan="2"><input type="text" name="Medida1_Estado" placeholder="Pendiente/Realizada"></td>
            </tr>
            <tr>
                <td colspan="4"><input type="text" name="Medida2_Desc" class="input-left"></td>
                <td colspan="3"><input type="text" name="Medida2_Resp"></td>
                <td colspan="3"><input type="date" name="Medida2_Fecha"></td>
                <td colspan="2"><input type="text" name="Medida2_Estado" placeholder="Pendiente/Realizada"></td>
            </tr>
        </table>

        <!-- 8. RESPONSABLES -->
        <table class="excel-table">
            <tr><td colspan="12" class="section-title">RESPONSABLES DEL REGISTRO Y LA INVESTIGACIÓN</td></tr>
            <tr>
                <th colspan="5">NOMBRE Y APELLIDOS</th>
                <th colspan="4">CARGO</th>
                <th colspan="3">FECHA</th>
            </tr>
            <tr>
                <td colspan="5"><input type="text" name="Responsable1_Nombre" class="input-left"></td>
                <td colspan="4"><input type="text" name="Responsable1_Cargo"></td>
                <td colspan="3"><input type="date" name="Responsable1_Fecha"></td>
            </tr>
            <tr>
                <td colspan="5"><input type="text" name="Responsable2_Nombre" class="input-left"></td>
                <td colspan="4"><input type="text" name="Responsable2_Cargo"></td>
                <td colspan="3"><input type="date" name="Responsable2_Fecha"></td>
            </tr>
        </table>

        <!-- BOTONES -->
        <div class="btn-container">
            <button type="submit" class="btn btn-save" id="btnGuardar">
                <i class="fas fa-save"></i> Guardar / Actualizar
            </button>
            <button type="button" class="btn btn-print" onclick="window.print()">
                <i class="fas fa-file-pdf"></i> Imprimir PDF
            </button>
            <button type="button" class="btn btn-clear" onclick="limpiarFormulario()">
                <i class="fas fa-eraser"></i> Limpiar
            </button>
        </div>
    </form>

    <!-- HISTORIAL -->
    <div class="admin-section">
        <div class="card">
            <div class="card-header">
                <h2 class="card-title"><i class="fas fa-history"></i> Historial de Registros</h2>
                <button type="button" class="btn btn-update" onclick="cargarTabla()" style="padding: 8px 16px; font-size: 12px;">
                    <i class="fas fa-sync-alt"></i> Actualizar Tabla
                </button>
            </div>
            <div class="table-responsive">
                <table class="admin-table" id="tablaRegistros">
                    <thead>
                        <tr>
                            <th>Nº Registro</th>
                            <th>Fecha Accidente</th>
                            <th>Trabajador</th>
                            <th>Gravedad</th>
                            <th style="text-align: center;">Acciones</th>
                        </tr>
                    </thead>
                    <tbody id="tbodyRegistros">
                        <tr><td colspan="5" class="empty-msg">Haz clic en "Actualizar Tabla" para cargar los datos...</td></tr>
                    </tbody>
                </table>
            </div>
        </div>
    </div>
</div>

<!-- LÓGICA JAVASCRIPT -->
<script>
    // ⚠️ PEGA AQUÍ TU URL DE GOOGLE APPS SCRIPT (Termina en /exec)
    const scriptURL = 'https://script.google.com/macros/s/AKfycbyRwBy95C-koQwaVmYRHieLEb5Z5JEwOcrsOWEdTCnyfXczstqRdJBBrQ41js5VkwZmZQ/exec';
    
    const form = document.getElementById('formAccidente');

    document.addEventListener('DOMContentLoaded', cargarTabla);

    function cargarTabla() {
        const tbody = document.getElementById('tbodyRegistros');
        tbody.innerHTML = '<tr><td colspan="5" class="empty-msg"><i class="fas fa-spinner fa-spin"></i> Cargando datos...</td></tr>';
        
        fetch(scriptURL + '?action=getData')
        .then(res => res.json())
        .then(data => {
            tbody.innerHTML = '';
            if (data.length === 0) {
                tbody.innerHTML = '<tr><td colspan="5" class="empty-msg">No hay registros guardados aún.</td></tr>';
                return;
            }
            data.reverse().forEach(row => {
                const tr = document.createElement('tr');
                
                let gravedadHTML = row.Gravedad || '-';
                if(row.Gravedad === 'Mortal') gravedadHTML = '<span style="color: #ef4444; font-weight: 700;">Mortal</span>';
                if(row.Gravedad === 'Incapacitante') gravedadHTML = '<span style="color: #f59e0b; font-weight: 700;">Incapacitante</span>';
                if(row.Gravedad === 'Leve') gravedadHTML = '<span style="color: #10b981; font-weight: 700;">Leve</span>';

                tr.innerHTML = `
                    <td style="font-weight: 700; color: #2563eb;">${row.NumRegistro || '-'}</td>
                    <td style="font-weight: 500;">${row.FechaAccidente || '-'}</td>
                    <td style="font-weight: 500;">${row.ApellidosNombres || '-'}</td>
                    <td>${gravedadHTML}</td>
                    <td>
                        <div class="action-btns">
                            <button class="btn-action btn-edit" onclick='cargarParaEditar(${JSON.stringify(row).replace(/'/g, "&#39;")})' title="Editar Registro">
                                <i class="fas fa-pen"></i> Editar
                            </button>
                            <button class="btn-action btn-del" onclick="eliminarRegistro('${row.NumRegistro}')" title="Eliminar Registro">
                                <i class="fas fa-trash-alt"></i> Eliminar
                            </button>
                        </div>
                    </td>
                `;
                tbody.appendChild(tr);
            });
        })
        .catch(err => {
            tbody.innerHTML = '<tr><td colspan="5" class="empty-msg" style="color: #ef4444;">Error al cargar datos.</td></tr>';
        });
    }

    form.addEventListener('submit', e => {
        e.preventDefault(); 
        const numReg = document.getElementById('NumRegistro').value;
        if (!numReg) return alert('Por favor, ingresa un Nº de Registro (Ej. 001).');

        const btnGuardar = document.getElementById('btnGuardar');
        const originalHTML = btnGuardar.innerHTML;
        btnGuardar.innerHTML = '<i class="fas fa-spinner fa-spin"></i> Guardando...';
        btnGuardar.disabled = true;

        fetch(scriptURL, { method: 'POST', body: new FormData(form) })
        .then(response => response.json())
        .then(data => {
            if (data.result === 'updated') alert('✅ ¡Registro EDITADO correctamente!');
            else if (data.result === 'created') alert('✅ ¡Nuevo registro GUARDADO correctamente!');
            else alert('⚠️ Hubo un problema: ' + JSON.stringify(data));
            
            btnGuardar.innerHTML = originalHTML;
            btnGuardar.disabled = false;
            cargarTabla(); 
        })
        .catch(error => {
            alert('❌ Error de conexión: ' + error.message);
            btnGuardar.innerHTML = originalHTML;
            btnGuardar.disabled = false;
        });
    });

    function cargarParaEditar(row) {
        for (let key in row) {
            const input = form.elements[key];
            if (input) {
                if (input.type === 'radio') {
                    if (input.value === row[key]) input.checked = true;
                } else if (input.type === 'checkbox') {
                    input.checked = (row[key] === 'Sí');
                } else {
                    input.value = row[key];
                }
            }
        }
        window.scrollTo({ top: 0, behavior: 'smooth' });
    }

    function eliminarRegistro(numRegistro) {
        if(!numRegistro || numRegistro === 'undefined') return alert('Nº de registro inválido.');
        if (confirm('¿Estás seguro de ELIMINAR el registro Nº ' + numRegistro + '?')) {
            const formData = new FormData();
            formData.append('action', 'delete');
            formData.append('NumRegistro', numRegistro);

            fetch(scriptURL, { method: 'POST', body: formData })
            .then(res => res.json())
            .then(data => {
                if (data.result === 'deleted') {
                    alert('🗑️ Registro eliminado.');
                    cargarTabla(); 
                } else {
                    alert('No se pudo eliminar el registro.');
                }
            });
        }
    }

    function limpiarFormulario() {
        if(confirm('¿Borrar todo lo escrito en el formulario?')) {
            form.reset();
            window.scrollTo({ top: 0, behavior: 'smooth' });
        }
    }
</script>

</body>
</html>

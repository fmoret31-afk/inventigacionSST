<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Registro de Accidentes - RM 050-2013-TR</title>
    <style>
        body { font-family: Arial, sans-serif; font-size: 12px; margin: 20px; color: #000; background-color: #f4f4f4;}
        .container { max-width: 1000px; margin: 0 auto; border: 2px solid #000; padding: 15px; background-color: #fff;}
        h1 { text-align: center; font-size: 16px; text-transform: uppercase; margin-bottom: 5px; }
        .header-top { display: flex; justify-content: space-between; margin-bottom: 15px; font-weight: bold; }
        fieldset { border: 1px solid #666; margin-bottom: 10px; padding: 10px; }
        legend { font-weight: bold; color: #fff; background-color: #333; padding: 3px 8px; font-size: 12px; }
        .row { display: flex; flex-wrap: wrap; margin-bottom: 5px; }
        .col { flex: 1; min-width: 150px; padding: 2px 5px; display: flex; align-items: center; }
        .col label { font-weight: bold; margin-right: 5px; white-space: nowrap; }
        input[type="text"], input[type="date"], input[type="time"], input[type="number"], select {
            width: 100%; border: none; border-bottom: 1px solid #000; background: transparent; font-family: Arial; font-size: 12px; padding: 2px;
        }
        input:focus, select:focus { outline: none; border-bottom: 2px solid #4a86e8; background-color: #f0f8ff; }
        textarea { width: 100%; height: 80px; border: 1px solid #000; font-family: Arial; font-size: 12px; padding: 5px; resize: vertical; }
        .checkbox-group { display: flex; align-items: center; gap: 15px; flex-wrap: wrap; margin-top: 5px;}
        table { width: 100%; border-collapse: collapse; margin-top: 5px; }
        th, td { border: 1px solid #000; padding: 5px; text-align: left; font-size: 11px; }
        th { background-color: #e0e0e0; text-align: center; }
        .btn-container { display: flex; justify-content: center; gap: 20px; margin-top: 20px; }
        .btn { padding: 10px 20px; font-size: 16px; font-weight: bold; cursor: pointer; border: none; border-radius: 5px; color: white;}
        .btn-save { background-color: #4a86e8; }
        .btn-save:hover { background-color: #3b6ebf; }
        .btn-print { background-color: #28a745; }
        .btn-print:hover { background-color: #218838; }
        @media print {
            .btn-container { display: none; }
            .container { border: none; padding: 0; }
            body { background-color: #fff; }
        }
    </style>
</head>
<body>

<div class="container">
    <div class="header-top">
        <div>Nº REGISTRO: <input type="text" name="NumRegistro" style="width: 150px;"></div>
        <div>Formato RM 050-2013-TR</div>
    </div>
    <h1>REGISTRO DE ACCIDENTES DE TRABAJO</h1>

    <form id="formAccidente">
        <fieldset>
            <legend>DATOS DEL EMPLEADOR PRINCIPAL</legend>
            <div class="row">
                <div class="col" style="flex: 2;"><label>Razón Social:</label> <input type="text" name="RazonSocial"></div>
                <div class="col"><label>RUC:</label> <input type="text" name="RUC"></div>
            </div>
            <div class="row">
                <div class="col" style="flex: 3;"><label>Domicilio:</label> <input type="text" name="Domicilio"></div>
                <div class="col" style="flex: 2;"><label>Actividad Económica:</label> <input type="text" name="ActividadEconomica"></div>
                <div class="col"><label>Nº Trabajadores:</label> <input type="number" name="NumTrabajadores"></div>
            </div>
        </fieldset>

        <fieldset>
            <legend>DATOS DEL TRABAJADOR ACCIDENTADO</legend>
            <div class="row">
                <div class="col" style="flex: 3;"><label>Apellidos y Nombres:</label> <input type="text" name="ApellidosNombres"></div>
                <div class="col"><label>DNI/CE:</label> <input type="text" name="DNI"></div>
                <div class="col"><label>Edad:</label> <input type="number" name="Edad"></div>
            </div>
            <div class="row">
                <div class="col"><label>Área:</label> <input type="text" name="Area"></div>
                <div class="col"><label>Puesto:</label> <input type="text" name="Puesto"></div>
                <div class="col"><label>Antigüedad:</label> <input type="text" name="Antiguedad"></div>
                <div class="col"><label>Sexo:</label> <input type="text" name="Sexo" placeholder="F/M"></div>
                <div class="col"><label>Turno:</label> <input type="text" name="Turno" placeholder="D/T/N"></div>
            </div>
            <div class="row">
                <div class="col"><label>Contrato:</label> <input type="text" name="TipoContrato"></div>
                <div class="col"><label>Experiencia:</label> <input type="text" name="Experiencia"></div>
                <div class="col"><label>Horas Trabajadas:</label> <input type="number" name="HorasTrabajadas"></div>
            </div>
        </fieldset>

        <fieldset>
            <legend>INVESTIGACIÓN DEL ACCIDENTE DE TRABAJO</legend>
            <div class="row">
                <div class="col"><label>Fecha Accidente:</label> <input type="date" name="FechaAccidente"></div>
                <div class="col"><label>Hora Accidente:</label> <input type="time" name="HoraAccidente"></div>
                <div class="col" style="flex: 2;"><label>Lugar exacto:</label> <input type="text" name="LugarExacto"></div>
            </div>
            
            <div style="margin-top: 10px; font-weight: bold;">GRAVEDAD DEL ACCIDENTE:</div>
            <div class="row">
                <div class="col" style="flex: 1;">
                    <select name="Gravedad">
                        <option value="">Seleccione...</option>
                        <option value="Leve">Accidente Leve</option>
                        <option value="Incapacitante">Accidente Incapacitante</option>
                        <option value="Mortal">Accidente Mortal</option>
                    </select>
                </div>
            </div>

            <div style="margin-top: 5px; font-weight: bold;">GRADO INCAPACITANTE (Si aplica):</div>
            <div class="checkbox-group">
                <label><input type="checkbox" name="TotalTemporal" value="Sí"> Total Temporal</label>
                <label><input type="checkbox" name="ParcialTemporal" value="Sí"> Parcial Temporal</label>
                <label><input type="checkbox" name="ParcialPermanente" value="Sí"> Parcial Permanente</label>
                <label><input type="checkbox" name="TotalPermanente" value="Sí"> Total Permanente</label>
            </div>

            <div class="row" style="margin-top: 10px;">
                <div class="col"><label>Días Descanso Médico:</label> <input type="number" name="DiasDescanso"></div>
                <div class="col"><label>Trabajadores Afectados:</label> <input type="number" name="TrabajadoresAfectados"></div>
                <div class="col" style="flex: 2;"><label>Parte del cuerpo lesionado:</label> <input type="text" name="ParteCuerpo"></div>
            </div>
        </fieldset>

        <fieldset>
            <legend>DESCRIPCIÓN DEL ACCIDENTE DE TRABAJO</legend>
            <textarea name="Descripcion" placeholder="Describa sólo los hechos comprobables..."></textarea>
        </fieldset>

        <fieldset>
            <legend>DESCRIPCIÓN DE LAS CAUSAS QUE ORIGINARON EL ACCIDENTE</legend>
            <textarea name="Causas" placeholder="Use el modelo de causalidad: Actos, Condiciones, Factores Personales, Factores de Trabajo, Fallas de Control..."></textarea>
        </fieldset>

        <fieldset>
            <legend>MEDIDAS CORRECTIVAS</legend>
            <table>
                <thead>
                    <tr>
                        <th style="width: 50%;">DESCRIPCIÓN DE LA MEDIDA</th>
                        <th style="width: 20%;">RESPONSABLE</th>
                        <th style="width: 15%;">FECHA EJECUCIÓN</th>
                        <th style="width: 15%;">ESTADO</th>
                    </tr>
                </thead>
                <tbody>
                    <tr>
                        <td><input type="text" name="Medida1_Desc" style="border:none; width:100%;"></td>
                        <td><input type="text" name="Medida1_Resp" style="border:none; width:100%;"></td>
                        <td><input type="date" name="Medida1_Fecha" style="border:none; width:100%;"></td>
                        <td><input type="text" name="Medida1_Estado" style="border:none; width:100%;"></td>
                    </tr>
                    <tr>
                        <td><input type="text" name="Medida2_Desc" style="border:none; width:100%;"></td>
                        <td><input type="text" name="Medida2_Resp" style="border:none; width:100%;"></td>
                        <td><input type="date" name="Medida2_Fecha" style="border:none; width:100%;"></td>
                        <td><input type="text" name="Medida2_Estado" style="border:none; width:100%;"></td>
                    </tr>
                </tbody>
            </table>
        </fieldset>

        <fieldset>
            <legend>RESPONSABLES DEL REGISTRO Y DE LA INVESTIGACIÓN</legend>
            <div class="row">
                <div class="col" style="flex: 2;"><label>Nombre:</label> <input type="text" name="Responsable"></div>
                <div class="col" style="flex: 1;"><label>Cargo:</label> <input type="text" name="CargoResponsable"></div>
                <div class="col"><label>Fecha:</label> <input type="date" name="FechaRegistro"></div>
            </div>
        </fieldset>
        
        <div class="btn-container">
            <button type="submit" class="btn btn-save">💾 Guardar en Google Sheets</button>
            <button type="button" class="btn btn-print" onclick="window.print()">🖨️ Imprimir / Guardar PDF</button>
        </div>
    </form>
</div>

<script>
    // Tu URL de API ya está configurada aquí:
    const scriptURL = 'https://script.google.com/macros/s/AKfycbyRwBy95C-koQwaVmYRHieLEb5Z5JEwOcrsOWEdTCnyfXczstqRdJBBrQ41js5VkwZmZQ/exec';

    const form = document.getElementById('formAccidente');

    form.addEventListener('submit', e => {
        e.preventDefault(); 
        
        const btnSave = document.querySelector('.btn-save');
        const textoOriginal = btnSave.innerText;
        btnSave.innerText = 'Guardando...';
        btnSave.disabled = true;

        // Enviar datos a Google Sheets
        fetch(scriptURL, {
            method: 'POST',
            body: new FormData(form)
        })
        .then(response => {
            alert('¡Datos guardados en Google Sheets correctamente!');
            form.reset(); 
            btnSave.innerText = textoOriginal;
            btnSave.disabled = false;
        })
        .catch(error => {
            alert('Error al guardar: ' + error.message);
            btnSave.innerText = textoOriginal;
            btnSave.disabled = false;
        });
    });
</script>

</body>
</html>

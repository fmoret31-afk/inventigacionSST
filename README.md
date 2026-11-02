<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Registro de Accidentes de Trabajo - RM 050-2013-TR</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=IBM+Plex+Sans:wght@400;500;600;700&display=swap" rel="stylesheet">
<style>
:root{--ink:#14213d;--line:#9aa5b8;--soft:#eef1f6;--mute:#5b6478;--accent:#d9480f;--ok:#2f9e44;--bad:#c92a2a}
*{box-sizing:border-box}
body{margin:0;padding:20px 10px 40px;background:#dfe4ec;font:11px/1.3 'IBM Plex Sans',Arial,sans-serif;color:var(--ink)}
.sheet{width:210mm;max-width:100%;margin:0 auto;background:#fff;padding:8mm;box-shadow:0 8px 30px rgba(20,33,61,.18)}

/* Cabecera */
.head{display:grid;grid-template-columns:1fr auto;align-items:end;border-bottom:3px solid var(--accent);padding-bottom:5px;margin-bottom:6px}
.head h1{margin:0;font-size:16px;font-weight:700;letter-spacing:.2px}
.head small{color:var(--mute);font-size:9px}
.nreg{display:flex;align-items:center;gap:6px;font-weight:600;font-size:11px}
.nreg input{width:80px;border:1.5px solid var(--ink);border-radius:3px;text-align:center;font-weight:700;color:var(--accent);font-size:12px}

/* Rejilla de 12 columnas con líneas finas */
.g{display:grid;grid-template-columns:repeat(12,1fr);gap:1px;background:var(--line);border:1px solid var(--line);margin-bottom:5px}
.g>*{background:#fff;min-width:0}
.sec{grid-column:span 12;background:var(--ink)!important;color:#fff;font-weight:600;font-size:10px;padding:3px 7px}
.sub{grid-column:span 12;background:var(--soft)!important;color:var(--mute);font-size:8.5px;padding:2px 7px;font-style:italic}
.f{padding:2px 5px 3px;display:flex;flex-direction:column}
.f>label,.f>.l{font-size:8px;color:var(--mute);font-weight:500;margin-bottom:1px}
.s2{grid-column:span 2}.s3{grid-column:span 3}.s4{grid-column:span 4}.s5{grid-column:span 5}.s6{grid-column:span 6}.s12{grid-column:span 12}
.s1{grid-column:span 1}

input[type=text],input[type=date],input[type=time],input[type=number],textarea{
  width:100%;border:0;border-bottom:1px dotted #c3cad8;background:transparent;font:500 11px 'IBM Plex Sans',Arial,sans-serif;color:var(--ink);padding:1px 0;border-radius:0}
input:focus,textarea:focus{outline:none;border-bottom:1px solid var(--accent);background:#fff7f2}
input::placeholder,textarea::placeholder{color:#b4bccb;font-weight:400}
.dt{display:flex;gap:4px}
textarea{resize:none;overflow:hidden;min-height:34px;line-height:1.35;font-weight:400;border:0}
.hint{font-size:8px;color:var(--mute);font-style:italic}

.opts{display:flex;flex-wrap:wrap;gap:2px 8px;padding-top:1px}
.opts label{display:inline-flex;align-items:center;gap:3px;font-size:9px;font-weight:500;color:var(--ink);cursor:pointer;white-space:nowrap}
.opts input{margin:0;width:11px;height:11px;accent-color:var(--accent)}

/* Botones */
.btns{display:flex;justify-content:center;flex-wrap:wrap;gap:10px;margin:12px 0 0}
.btn{display:inline-flex;align-items:center;gap:6px;padding:9px 18px;font:600 12px 'IBM Plex Sans',sans-serif;border:0;border-radius:5px;color:#fff;cursor:pointer}
.btn:hover{filter:brightness(1.08)}.btn:disabled{opacity:.6;cursor:wait}
.b-save{background:var(--ok)}.b-print{background:var(--ink)}.b-clear{background:var(--bad)}.b-sync{background:var(--accent);padding:6px 12px;font-size:11px}

/* Historial */
.hist{width:210mm;max-width:100%;margin:18px auto 0;background:#fff;border:1px solid var(--line);border-radius:6px;overflow:hidden}
.hist header{display:flex;justify-content:space-between;align-items:center;padding:10px 14px;background:var(--soft);border-bottom:1px solid var(--line)}
.hist h2{margin:0;font-size:14px}
.tw{overflow-x:auto;padding:6px 14px 12px}
.hist table{width:100%;border-collapse:collapse;font-size:11px}
.hist th,.hist td{padding:7px 6px;text-align:left;border-bottom:1px solid #e3e7ef}
.hist th{font-size:10px;color:var(--mute);font-weight:600}
.hist td.c,.hist th.c{text-align:center}
.tag{font-weight:700}.t-Leve{color:var(--ok)}.t-Incapacitante{color:#e67700}.t-Mortal{color:var(--bad)}
.ab{border:0;border-radius:4px;padding:4px 9px;font:600 10px 'IBM Plex Sans',sans-serif;cursor:pointer;margin:0 2px}
.ab.e{background:#fff3bf;color:#8a5a00}.ab.d{background:#ffe3e3;color:#a61e1e}
.empty{text-align:center;color:var(--mute);font-style:italic;padding:16px!important}

/* Impresión: una sola hoja A4 */
@page{size:A4 portrait;margin:6mm}
@media print{
  body{background:#fff;padding:0;font-size:9.5px}
  .sheet{width:198mm;padding:0;box-shadow:none;margin:0}
  .btns,.hist,.hint{display:none!important}
  .g,.sec,.sub,.head{-webkit-print-color-adjust:exact;print-color-adjust:exact}
  input,textarea{border-bottom:0!important;background:transparent!important}
  input::placeholder,textarea::placeholder{color:transparent}
  .nreg input{border:1.5px solid var(--ink)!important}
}
</style>
</head>
<body>

<form id="formAccidente" class="sheet" autocomplete="off">

  <div class="head">
    <div>
      <h1>Registro de accidentes de trabajo</h1>
      <small>Formato RM 050-2013-TR</small>
    </div>
    <div class="nreg">Nº registro <input type="text" name="NumRegistro" id="NumRegistro" placeholder="001"></div>
  </div>

  <!-- Empleador principal -->
  <div class="g">
    <div class="sec">Datos del empleador principal</div>
    <div class="f s4"><label>Razón social o denominación</label><input type="text" name="RazonSocial"></div>
    <div class="f s2"><label>RUC</label><input type="text" name="RUC"></div>
    <div class="f s3"><label>Domicilio</label><input type="text" name="Domicilio"></div>
    <div class="f s2"><label>Actividad económica</label><input type="text" name="ActividadEconomica"></div>
    <div class="f s1"><label>N.º trabaj.</label><input type="number" name="NumTrabajadores"></div>
    <div class="sub">Completar sólo en caso de alto riesgo</div>
    <div class="f s4"><label>Afiliados al SCTR</label><input type="number" name="SCTR_Afiliados"></div>
    <div class="f s4"><label>No afiliados al SCTR</label><input type="number" name="SCTR_NoAfiliados"></div>
    <div class="f s4"><label>Aseguradora</label><input type="text" name="Aseguradora" placeholder="Ej. Pacífico"></div>
  </div>

  <!-- Contratista -->
  <div class="g">
    <div class="sec">Empleador de intermediación / contratista</div>
    <div class="f s4"><label>Razón social</label><input type="text" name="Contratista_RazonSocial"></div>
    <div class="f s2"><label>RUC</label><input type="text" name="Contratista_RUC"></div>
    <div class="f s3"><label>Domicilio</label><input type="text" name="Contratista_Domicilio"></div>
    <div class="f s2"><label>Actividad económica</label><input type="text" name="Contratista_Actividad"></div>
    <div class="f s1"><label>N.º trabaj.</label><input type="number" name="Contratista_NumTrabajadores"></div>
    <div class="sub">Completar sólo en caso de alto riesgo</div>
    <div class="f s4"><label>Afiliados al SCTR</label><input type="number" name="Contratista_SCTR_Afiliados"></div>
    <div class="f s4"><label>No afiliados al SCTR</label><input type="number" name="Contratista_SCTR_NoAfiliados"></div>
    <div class="f s4"><label>Aseguradora</label><input type="text" name="Contratista_Aseguradora"></div>
  </div>

  <!-- Trabajador -->
  <div class="g">
    <div class="sec">Datos del trabajador accidentado</div>
    <div class="f s6"><label>Apellidos y nombres</label><input type="text" name="ApellidosNombres"></div>
    <div class="f s3"><label>DNI / CE</label><input type="text" name="DNI"></div>
    <div class="f s1"><label>Edad</label><input type="number" name="Edad"></div>
    <div class="f s2"><label>Horas trabajadas</label><input type="number" name="HorasTrabajadas"></div>
    <div class="f s2"><label>Área</label><input type="text" name="Area"></div>
    <div class="f s2"><label>Puesto</label><input type="text" name="Puesto"></div>
    <div class="f s2"><label>Antigüedad</label><input type="text" name="Antiguedad"></div>
    <div class="f s1"><label>Sexo F/M</label><input type="text" name="Sexo" maxlength="1"></div>
    <div class="f s1"><label>Turno D/T/N</label><input type="text" name="Turno" maxlength="1"></div>
    <div class="f s2"><label>Contrato</label><input type="text" name="TipoContrato"></div>
    <div class="f s2"><label>Experiencia</label><input type="text" name="Experiencia"></div>
  </div>

  <!-- Investigación -->
  <div class="g">
    <div class="sec">Investigación del accidente</div>
    <div class="f s4"><label>Fecha y hora del accidente</label>
      <div class="dt"><input type="date" name="FechaAccidente"><input type="time" name="HoraAccidente" style="width:70px"></div></div>
    <div class="f s3"><label>Inicio de la investigación</label><input type="date" name="FechaInvestigacion"></div>
    <div class="f s5"><label>Lugar exacto</label><input type="text" name="LugarExacto"></div>
    <div class="f s3"><span class="l">Gravedad</span>
      <div class="opts">
        <label><input type="radio" name="Gravedad" value="Leve">Leve</label>
        <label><input type="radio" name="Gravedad" value="Incapacitante">Incapacitante</label>
        <label><input type="radio" name="Gravedad" value="Mortal">Mortal</label>
      </div></div>
    <div class="f s5"><span class="l">Grado incapacitante</span>
      <div class="opts">
        <label><input type="checkbox" name="TotalTemporal" value="Sí">Total temporal</label>
        <label><input type="checkbox" name="ParcialTemporal" value="Sí">Parcial temporal</label>
        <label><input type="checkbox" name="ParcialPermanente" value="Sí">Parcial permanente</label>
        <label><input type="checkbox" name="TotalPermanente" value="Sí">Total permanente</label>
      </div></div>
    <div class="f s2"><label>Días de descanso</label><input type="number" name="DiasDescanso"></div>
    <div class="f s2"><label>Trabaj. afectados</label><input type="number" name="TrabajadoresAfectados"></div>
    <div class="f s12"><label>Parte del cuerpo lesionado</label><input type="text" name="ParteCuerpo"></div>
  </div>

  <!-- Descripción y causas -->
  <div class="g">
    <div class="sec">Descripción del accidente</div>
    <div class="f s12"><span class="hint">Describa sólo hechos comprobables. Adjunte declaraciones y procedimientos.</span>
      <textarea name="Descripcion" placeholder="Relato cronológico del accidente…"></textarea></div>
    <div class="sec">Causas que originaron el accidente</div>
    <div class="f s12"><span class="hint">Use el modelo de causalidad: inmediatas, básicas y fallas de control.</span>
      <textarea name="Causas" placeholder="Análisis de causas…"></textarea></div>
  </div>

  <!-- Medidas correctivas -->
  <div class="g">
    <div class="sec">Medidas correctivas</div>
    <div class="f s5"><label>Descripción de la medida</label><input type="text" name="Medida1_Desc"></div>
    <div class="f s3"><label>Responsable</label><input type="text" name="Medida1_Resp"></div>
    <div class="f s2"><label>Fecha de ejecución</label><input type="date" name="Medida1_Fecha"></div>
    <div class="f s2"><label>Estado</label><input type="text" name="Medida1_Estado" placeholder="Pendiente"></div>
    <div class="f s5"><input type="text" name="Medida2_Desc"></div>
    <div class="f s3"><input type="text" name="Medida2_Resp"></div>
    <div class="f s2"><input type="date" name="Medida2_Fecha"></div>
    <div class="f s2"><input type="text" name="Medida2_Estado" placeholder="Realizada"></div>
  </div>

  <!-- Responsables -->
  <div class="g" style="margin-bottom:0">
    <div class="sec">Responsables del registro y la investigación</div>
    <div class="f s5"><label>Nombre y apellidos</label><input type="text" name="Responsable1_Nombre"></div>
    <div class="f s4"><label>Cargo</label><input type="text" name="Responsable1_Cargo"></div>
    <div class="f s3"><label>Fecha</label><input type="date" name="Responsable1_Fecha"></div>
    <div class="f s5"><input type="text" name="Responsable2_Nombre"></div>
    <div class="f s4"><input type="text" name="Responsable2_Cargo"></div>
    <div class="f s3"><input type="date" name="Responsable2_Fecha"></div>
  </div>

  <div class="btns">
    <button type="submit" class="btn b-save" id="btnGuardar">Guardar / actualizar</button>
    <button type="button" class="btn b-print" onclick="window.print()">Imprimir A4</button>
    <button type="button" class="btn b-clear" onclick="limpiarFormulario()">Limpiar</button>
  </div>
</form>

<!-- Historial -->
<section class="hist">
  <header>
    <h2>Historial de registros</h2>
    <button type="button" class="btn b-sync" onclick="cargarTabla()">Actualizar tabla</button>
  </header>
  <div class="tw">
    <table>
      <thead><tr><th>Nº registro</th><th>Fecha</th><th>Trabajador</th><th>Gravedad</th><th class="c">Acciones</th></tr></thead>
      <tbody id="tbodyRegistros"><tr><td colspan="5" class="empty">Cargando…</td></tr></tbody>
    </table>
  </div>
</section>

<script>
// Pega aquí la URL de tu Web App de Apps Script (termina en /exec)
const scriptURL = 'https://script.google.com/macros/s/AKfycbyFofL-a1zNqapPuL3sPNWMWZBmsAcLRsyXaxpd2YwlI1o5NDPlULEsKPwuw1-MXc0aUA/exec';

const form = document.getElementById('formAccidente');
const tbody = document.getElementById('tbodyRegistros');
let registros = [];

const esc = s => String(s ?? '').replace(/[&<>"']/g, c => ({'&':'&amp;','<':'&lt;','>':'&gt;','"':'&quot;',"'":'&#39;'}[c]));

/* Las cajas de texto largas crecen según el contenido */
function autoGrow(t){ t.style.height = 'auto'; t.style.height = t.scrollHeight + 'px'; }
document.querySelectorAll('textarea').forEach(t => t.addEventListener('input', () => autoGrow(t)));

/* Impresión: reduce la escala lo necesario para que todo entre en una hoja A4 */
const MM = 3.7795;
window.addEventListener('beforeprint', () => {
  document.querySelectorAll('textarea').forEach(autoGrow);
  form.style.cssText = 'width:198mm;padding:0;zoom:1';
  const h = form.scrollHeight - document.querySelector('.btns').offsetHeight;
  const z = Math.min(1, (285 * MM) / h);
  form.style.zoom = z;
});
window.addEventListener('afterprint', () => form.removeAttribute('style'));

function cargarTabla() {
  tbody.innerHTML = '<tr><td colspan="5" class="empty">Cargando datos…</td></tr>';
  fetch(scriptURL + '?action=getData')
    .then(r => r.json())
    .then(data => {
      registros = data.reverse();
      if (!registros.length) {
        tbody.innerHTML = '<tr><td colspan="5" class="empty">Aún no hay registros guardados.</td></tr>';
        return;
      }
      tbody.innerHTML = registros.map((r, i) => `
        <tr>
          <td><b>${esc(r.NumRegistro) || '-'}</b></td>
          <td>${esc(r.FechaAccidente) || '-'}</td>
          <td>${esc(r.ApellidosNombres) || '-'}</td>
          <td><span class="tag t-${esc(r.Gravedad)}">${esc(r.Gravedad) || '-'}</span></td>
          <td class="c">
            <button class="ab e" data-i="${i}" data-a="edit">Editar</button>
            <button class="ab d" data-i="${i}" data-a="del">Eliminar</button>
          </td>
        </tr>`).join('');
    })
    .catch(() => {
      tbody.innerHTML = '<tr><td colspan="5" class="empty" style="color:#c92a2a">No se pudieron cargar los datos. Revisa la URL del script.</td></tr>';
    });
}

tbody.addEventListener('click', e => {
  const b = e.target.closest('button[data-a]');
  if (!b) return;
  const row = registros[+b.dataset.i];
  if (b.dataset.a === 'edit') cargarParaEditar(row);
  else eliminarRegistro(row.NumRegistro);
});

form.addEventListener('submit', e => {
  e.preventDefault();
  if (!form.NumRegistro.value.trim()) return alert('Ingresa un Nº de registro (ej. 001).');

  const btn = document.getElementById('btnGuardar');
  const txt = btn.textContent;
  btn.textContent = 'Guardando…';
  btn.disabled = true;

  fetch(scriptURL, { method: 'POST', body: new FormData(form) })
    .then(r => r.json())
    .then(d => {
      if (d.result === 'updated') alert('Registro actualizado.');
      else if (d.result === 'created') alert('Registro guardado.');
      else alert('Hubo un problema: ' + JSON.stringify(d));
      cargarTabla();
    })
    .catch(err => alert('Error de conexión: ' + err.message))
    .finally(() => { btn.textContent = txt; btn.disabled = false; });
});

function cargarParaEditar(row) {
  form.reset();
  for (const key in row) {
    const els = form.elements[key];
    if (!els) continue;
    const val = row[key] ?? '';
    if (els instanceof RadioNodeList) {
      els.forEach(r => r.checked = (r.value === val));
    } else if (els.type === 'checkbox') {
      els.checked = (val === 'Sí');
    } else {
      els.value = val;
    }
  }
  document.querySelectorAll('textarea').forEach(autoGrow);
  window.scrollTo({ top: 0, behavior: 'smooth' });
}

function eliminarRegistro(num) {
  if (!num) return alert('Nº de registro inválido.');
  if (!confirm('¿Eliminar el registro Nº ' + num + '?')) return;
  const fd = new FormData();
  fd.append('action', 'delete');
  fd.append('NumRegistro', num);
  fetch(scriptURL, { method: 'POST', body: fd })
    .then(r => r.json())
    .then(d => {
      if (d.result === 'deleted') cargarTabla();
      else alert('No se pudo eliminar el registro.');
    })
    .catch(err => alert('Error de conexión: ' + err.message));
}

function limpiarFormulario() {
  if (!confirm('¿Borrar todo lo escrito en el formulario?')) return;
  form.reset();
  document.querySelectorAll('textarea').forEach(autoGrow);
  window.scrollTo({ top: 0, behavior: 'smooth' });
}

document.addEventListener('DOMContentLoaded', cargarTabla);
</script>
</body>
</html>

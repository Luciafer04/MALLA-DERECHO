<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8">
  <title>Malla Curricular Derecho - Universidad de Lima</title>
  <style>
    body { font-family: Arial, sans-serif; background: #f8fafc; }
    .malla {
      display: grid;
      grid-template-columns: repeat(6, 220px);
      grid-auto-rows: 90px;
      grid-gap: 14px;
      margin: 30px auto;
      max-width: 1400px;
      background: #fff;
      border-radius: 12px;
      padding: 20px 20px 40px 20px;
      box-shadow: 0 2px 25px #bbb6;
    }
    .celda {
      background: #e0e7ff;
      border: 1px solid #64748b;
      padding: 15px 8px 5px 8px;
      text-align: center;
      border-radius: 9px;
      cursor: pointer;
      transition: background 0.2s, box-shadow 0.2s;
      font-size: 1.05em;
      position: relative;
      min-height: 60px;
      box-shadow: 1px 1px 8px #cbd5e1;
      overflow: visible;
    }
    .celda:hover {
      background: #a5b4fc;
      box-shadow: 2px 3px 12px #bac7e6;
    }
    .info {
      display: none;
      position: absolute;
      top: 105%;
      left: 0;
      background: #f1f5f9;
      border: 1px solid #64748b;
      padding: 12px 16px;
      z-index: 5;
      width: 320px;
      border-radius: 10px;
      box-shadow: 2px 2px 8px #aaa;
      text-align: left;
      font-size: 0.98em;
    }
    .celda.activa .info {
      display: block;
    }
    .ciclo {
      grid-column: span 6;
      background: #3b82f6;
      color: #fff;
      border: none;
      font-weight: bold;
      border-radius: 8px;
      padding: 10px 0 10px 12px;
      margin-bottom: 3px;
      text-align: left;
      font-size: 1.15em;
      letter-spacing: 0.5px;
      box-shadow: 0 2px 12px #93c5fd44;
    }
    .credito {
      font-size: 0.93em;
      color: #1e293b;
      margin-top: 7px;
      font-weight: 600;
    }
    .prereq {
      margin-top: 6px;
      color: #334155;
      font-size: 0.93em;
    }
    @media (max-width: 1200px) {
      .malla {
        grid-template-columns: repeat(2, 1fr);
      }
    }
    @media (max-width: 700px) {
      .malla {
        grid-template-columns: 1fr;
        padding: 10px;
      }
    }
  </style>
</head>
<body>
  <h2 style="text-align:center;margin-top:28px;margin-bottom:2px;">
    Malla Curricular de Derecho - Universidad de Lima (2025)
  </h2>
  <p style="text-align:center;margin-bottom:20px;">
    Haz clic en cada curso para ver créditos y prerrequisitos.<br>
    <a href="https://www.ulima.edu.pe/sites/default/files/2025-01/malla-derecho-2025.pdf" target="_blank">Malla oficial</a> &nbsp;|&nbsp;
    <a href="https://www.ulima.edu.pe/sites/default/files/page/file/6100_plan_de_estudios_2021-1.pdf" target="_blank">Prerrequisitos</a>
  </p>
  <div class="malla" id="malla"></div>
<script>
const malla = [
  {
    ciclo: "1er Ciclo",
    cursos: [
      { nombre: "Comunicación", creditos: 4, prereq: "" },
      { nombre: "Derecho Romano", creditos: 4, prereq: "" },
      { nombre: "Historia del Derecho", creditos: 3, prereq: "" },
      { nombre: "Introducción al Derecho", creditos: 4, prereq: "" },
      { nombre: "Lógica Jurídica", creditos: 3, prereq: "" },
      { nombre: "Ciencia Política", creditos: 3, prereq: "" },
    ]
  },
  {
    ciclo: "2do Ciclo",
    cursos: [
      { nombre: "Derecho Constitucional I", creditos: 4, prereq: "" },
      { nombre: "Derecho Civil I", creditos: 4, prereq: "" },
      { nombre: "Teoría General del Proceso", creditos: 4, prereq: "" },
      { nombre: "Filosofía del Derecho", creditos: 3, prereq: "" },
      { nombre: "Sociología Jurídica", creditos: 3, prereq: "" },
      { nombre: "Fundamentos de Economía", creditos: 3, prereq: "" },
    ]
  },
  {
    ciclo: "3er Ciclo",
    cursos: [
      { nombre: "Derecho Constitucional II", creditos: 4, prereq: "Derecho Constitucional I" },
      { nombre: "Derecho Civil II", creditos: 4, prereq: "Derecho Civil I" },
      { nombre: "Derecho Penal I", creditos: 4, prereq: "" },
      { nombre: "Derecho Procesal Civil I", creditos: 4, prereq: "Teoría General del Proceso" },
      { nombre: "Derecho Administrativo I", creditos: 4, prereq: "" },
      { nombre: "Derecho Empresarial I", creditos: 3, prereq: "" },
    ]
  },
  {
    ciclo: "4to Ciclo",
    cursos: [
      { nombre: "Derecho Civil III", creditos: 4, prereq: "Derecho Civil II" },
      { nombre: "Derecho Penal II", creditos: 4, prereq: "Derecho Penal I" },
      { nombre: "Derecho Procesal Civil II", creditos: 4, prereq: "Derecho Procesal Civil I" },
      { nombre: "Derecho Administrativo II", creditos: 4, prereq: "Derecho Administrativo I" },
      { nombre: "Derecho Empresarial II", creditos: 3, prereq: "Derecho Empresarial I" },
      { nombre: "Metodología de la Investigación Jurídica", creditos: 3, prereq: "" },
    ]
  },
  {
    ciclo: "5to Ciclo",
    cursos: [
      { nombre: "Derecho Civil IV", creditos: 4, prereq: "Derecho Civil III" },
      { nombre: "Derecho Penal III", creditos: 4, prereq: "Derecho Penal II" },
      { nombre: "Derecho Procesal Penal I", creditos: 4, prereq: "Teoría General del Proceso" },
      { nombre: "Derecho Laboral I", creditos: 4, prereq: "" },
      { nombre: "Derecho Internacional Público", creditos: 3, prereq: "" },
      { nombre: "Argumentación Jurídica", creditos: 3, prereq: "" },
    ]
  },
  {
    ciclo: "6to Ciclo",
    cursos: [
      { nombre: "Derecho Civil V", creditos: 4, prereq: "Derecho Civil IV" },
      { nombre: "Derecho Procesal Penal II", creditos: 4, prereq: "Derecho Procesal Penal I" },
      { nombre: "Derecho Laboral II", creditos: 4, prereq: "Derecho Laboral I" },
      { nombre: "Derecho Internacional Privado", creditos: 3, prereq: "Derecho Civil II" },
      { nombre: "Derecho Tributario I", creditos: 3, prereq: "" },
      { nombre: "Electivo I", creditos: 3, prereq: "" },
    ]
  },
  {
    ciclo: "7mo Ciclo",
    cursos: [
      { nombre: "Derecho de Familia", creditos: 4, prereq: "Derecho Civil V" },
      { nombre: "Derecho de Sucesiones", creditos: 4, prereq: "Derecho Civil V" },
      { nombre: "Derecho Procesal Constitucional", creditos: 4, prereq: "Derecho Constitucional II" },
      { nombre: "Derecho Tributario II", creditos: 3, prereq: "Derecho Tributario I" },
      { nombre: "Derecho de la Competencia y de la Propiedad Intelectual", creditos: 3, prereq: "" },
      { nombre: "Electivo II", creditos: 3, prereq: "" },
    ]
  },
  {
    ciclo: "8vo Ciclo",
    cursos: [
      { nombre: "Derecho Ambiental", creditos: 3, prereq: "" },
      { nombre: "Derecho Bancario y Financiero", creditos: 3, prereq: "" },
      { nombre: "Derecho de los Contratos", creditos: 4, prereq: "Derecho Civil V" },
      { nombre: "Derecho de los Seguros", creditos: 3, prereq: "" },
      { nombre: "Derecho Registral y Notarial", creditos: 3, prereq: "Derecho Civil III" },
      { nombre: "Electivo III", creditos: 3, prereq: "" },
    ]
  },
  {
    ciclo: "9no Ciclo",
    cursos: [
      { nombre: "Derecho Procesal Laboral", creditos: 4, prereq: "Derecho Laboral II" },
      { nombre: "Derecho Procesal de Familia", creditos: 4, prereq: "Derecho de Familia" },
      { nombre: "Derecho Procesal de Sucesiones", creditos: 4, prereq: "Derecho de Sucesiones" },
      { nombre: "Derecho Procesal Tributario", creditos: 4, prereq: "Derecho Tributario II" },
      { nombre: "Electivo IV", creditos: 3, prereq: "" },
      { nombre: "Electivo V", creditos: 3, prereq: "" },
    ]
  },
  {
    ciclo: "10mo Ciclo",
    cursos: [
      { nombre: "Seminario de Integración Jurídica", creditos: 5, prereq: "Haber aprobado todos los cursos obligatorios de los ciclos anteriores" },
      { nombre: "Práctica Preprofesional", creditos: 8, prereq: "Haber aprobado todos los cursos obligatorios de los ciclos anteriores" },
      { nombre: "Electivo VI", creditos: 3, prereq: "" },
      { nombre: "Electivo VII", creditos: 3, prereq: "" }
    ]
  }
];

// Renderizado
const grid = document.getElementById('malla');
malla.forEach(ciclo => {
  // Título del ciclo
  const cicloDiv = document.createElement('div');
  cicloDiv.className = 'ciclo';
  cicloDiv.textContent = ciclo.ciclo;
  grid.appendChild(cicloDiv);

  // Cursos del ciclo
  ciclo.cursos.forEach(curso => {
    const celda = document.createElement('div');
    celda.className = 'celda';
    celda.textContent = curso.nombre;
    const info = document.createElement('div');
    info.className = 'info';
    info.innerHTML = `<div class="credito"><b>Créditos:</b> ${curso.creditos}</div>` +
      (curso.prereq ? `<div class="prereq"><b>Prerrequisito:</b> ${curso.prereq}</div>` : '');
    celda.appendChild(info);
    celda.onclick = function(e) {
      // Cierra otras
      document.querySelectorAll('.celda.activa').forEach(c => c.classList.remove('activa'));
      celda.classList.toggle('activa');
      e.stopPropagation();
    };
    grid.appendChild(celda);
  });
});

// Cerrar info al hacer clic fuera
window.onclick = () => {
  document.querySelectorAll('.celda.activa').forEach(c => c.classList.remove('activa'));
};
</script>
</body>
</html>

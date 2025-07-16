<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8" />
  <title>Malla Curricular Interactiva</title>
  <style>
    body {
      font-family: sans-serif;
      background: #f4f4f4;
      margin: 0;
      padding: 20px;
    }
    h1 {
      text-align: center;
    }
    .semestre {
      margin-bottom: 20px;
    }
    .semestre h2 {
      background: #007acc;
      color: white;
      padding: 10px;
      border-radius: 5px;
    }
    .ramos {
      display: flex;
      flex-wrap: wrap;
      gap: 10px;
    }
    .ramo {
      padding: 10px 15px;
      background: #fff;
      border: 2px solid #ccc;
      border-radius: 6px;
      cursor: pointer;
      transition: all 0.2s ease-in-out;
      user-select: none;
    }
    .ramo:hover {
      background: #e6f7ff;
    }
    .ramo.aprobado {
      text-decoration: line-through;
      background: #d4edda;
      border-color: #28a745;
      color: #555;
      cursor: default;
    }
    .ramo.bloqueado {
      background: #eee;
      color: #999;
      border-color: #bbb;
      cursor: not-allowed;
    }
  </style>
</head>
<body>
  <h1>Malla Curricular - Carrera de Informática</h1>

  <div class="semestre">
    <h2>1º Semestre</h2>
    <div class="ramos">
      <div class="ramo" data-id="prog1">Programación I</div>
      <div class="ramo" data-id="mat1">Matemáticas I</div>
      <div class="ramo" data-id="introTI">Intro a TI</div>
    </div>
  </div>

  <div class="semestre">
    <h2>2º Semestre</h2>
    <div class="ramos">
      <div class="ramo bloqueado" data-id="prog2" data-prer="prog1">Programación II</div>
      <div class="ramo bloqueado" data-id="mat2" data-prer="mat1">Matemáticas II</div>
      <div class="ramo bloqueado" data-id="bd1" data-prer="prog1">Bases de Datos I</div>
    </div>
  </div>

  <div class="semestre">
    <h2>3º Semestre</h2>
    <div class="ramos">
      <div class="ramo bloqueado" data-id="estructuras" data-prer="prog2">Estructuras de Datos</div>
      <div class="ramo bloqueado" data-id="bd2" data-prer="bd1">Bases de Datos II</div>
    </div>
  </div>

  <div class="semestre">
    <h2>4º Semestre</h2>
    <div class="ramos">
      <div class="ramo bloqueado" data-id="poo" data-prer="estructuras">Programación Orientada a Objetos</div>
      <div class="ramo bloqueado" data-id="algoritmos" data-prer="estructuras">Análisis de Algoritmos</div>
    </div>
  </div>

  <script>
    const ramos = document.querySelectorAll('.ramo');

    ramos.forEach(ramo => {
      ramo.addEventListener('click', () => {
        if (ramo.classList.contains('bloqueado') || ramo.classList.contains('aprobado')) return;

        ramo.classList.add('aprobado');
        desbloquearRamos(ramo.dataset.id);
      });
    });

    function desbloquearRamos(idAprobado) {
      ramos.forEach(ramo => {
        const prer = ramo.dataset.prer;
        if (prer === idAprobado && ramo.classList.contains('bloqueado')) {
          ramo.classList.remove('bloqueado');
        }
      });
    }
  </script>
</body>
</html>

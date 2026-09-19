<template>
  <footer class="footer">
    <div class="divider"></div>
    <p class="project-name">Projeto de Extensão Acadêmica</p>
    <p class="institution">
      <a href="https://ebramec.edu.br" target="_blank" rel="noopener noreferrer">
        Faculdade EBRAMEC
       </a> 
       - Alunos do 5º Semestre Graduação em Acupuntura
    </p>
    <p class="copyright">&copy; 2026 — Idealização & Desenvolvimento Digital: {{ autorDigital }}</p>
  </footer>
</template>

<script setup>
  import {autorDigital}  from '../data/appData.js';
</script>

<style scoped>
.footer {
  width: 100%;
  max-width: 400px;
  margin-top: auto; 
  padding-top: 40px;
  padding-bottom: 10px;
  font-family: 'Georgia', serif;
  text-align: center;
}
.divider {
  height: 1px;
  background: linear-gradient(to right, transparent, #8b5a2b, transparent);
  margin-bottom: 15px;
  opacity: 0.4;
}
.project-name {
  font-size: 0.9rem;
  font-weight: bold;
  color: #1e4620; 
  margin: 0 0 4px 0;
  text-transform: uppercase;
  letter-spacing: 0.05em;
}
.institution {
  font-size: 0.85rem;
  color: #556b2f;
  margin: 0 0 8px 0;
  font-style: italic;
}

.team {
  font-size: 0.8rem;
  color: #3e2723;
  margin: 0 0 12px 0;
  line-height: 1.4;
}

.copyright {
  font-size: 0.7rem;
  color: #99571a;
  margin: 10px 0 0 0;
  opacity: 0.8;
}
.credits {
  margin: 15px 0 10px 0;
  padding: 0;
  text-align: center; 
}
.credit-line {
  font-size: 0.72rem; 
  color: #6d5c52; 
  line-height: 1.5;
  margin: 0 0 4px 0;
  font-weight: 300; 
  letter-spacing: 0.02em;
}
.credit-line strong {
  color: #4a3b32; 
  font-weight: 600;
}
@media (max-width: 480px) {
  .footer {
    padding-top: 20px;
  }
  .project-name {
    font-size: 0.8rem;
  }
  .institution {
    font-size: 0.75rem;
  }
   .footer {
    padding-top: 20px;
  }
  .project-name {
    font-size: 0.8rem;
  }
  .institution {
    font-size: 0.75rem;
  }
  .credit-line {
    font-size: 0.68rem;
  }
}
</style>

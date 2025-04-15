# SWIFT-SCORE
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Formulário SWIFT Score - UTI</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <script>
        tailwind.config = {
            darkMode: 'class',
            theme: {
                extend: {
                    colors: {
                        primary: '#5D5CDE',
                        'primary-dark': '#4a49b7'
                    }
                }
            }
        };

        // Detectar preferência de modo escuro
        if (window.matchMedia && window.matchMedia('(prefers-color-scheme: dark)').matches) {
            document.documentElement.classList.add('dark');
        }
        
        window.matchMedia('(prefers-color-scheme: dark)').addEventListener('change', event => {
            if (event.matches) {
                document.documentElement.classList.add('dark');
            } else {
                document.documentElement.classList.remove('dark');
            }
        });
    </script>
</head>
<body class="bg-white dark:bg-gray-900 text-gray-800 dark:text-gray-200 min-h-screen">
    <div class="container mx-auto p-4 max-w-4xl">
        <h1 class="text-2xl md:text-3xl font-bold text-center my-4 md:my-6 text-primary dark:text-primary">SWIFT Score - UTI</h1>
        
        <div class="flex justify-center mb-4">
            <button type="button" id="infoBtn" class="flex items-center gap-2 px-4 py-2 bg-blue-600 text-white rounded-md hover:bg-blue-700 focus:outline-none focus:ring-2 focus:ring-blue-600 focus:ring-offset-2">
                <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                    <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M13 16h-1v-4h-1m1-4h.01M21 12a9 9 0 11-18 0 9 9 0 0118 0z" />
                </svg>
                Informações sobre o SWIFT Score
            </button>
        </div>
        
        <!-- Formulário principal -->
        <div class="bg-white dark:bg-gray-800 rounded-lg shadow-md p-4 md:p-6 mb-6">
            <h2 class="text-lg md:text-xl font-semibold mb-4">Dados do Paciente</h2>
            
            <form id="swiftForm" class="space-y-4">
                <div class="grid grid-cols-1 md:grid-cols-2 gap-4">
                    <div>
                        <label for="nome" class="block text-sm font-medium mb-1">Nome do Paciente</label>
                        <input type="text" id="nome" name="nome" required 
                            class="w-full px-3 py-2 border border-gray-300 dark:border-gray-600 rounded-md text-base
                            dark:bg-gray-700 focus:outline-none focus:ring-2 focus:ring-primary">
                    </div>
                    <div>
                        <label for="registro" class="block text-sm font-medium mb-1">Registro Hospitalar</label>
                        <input type="text" id="registro" name="registro" required 
                            class="w-full px-3 py-2 border border-gray-300 dark:border-gray-600 rounded-md text-base
                            dark:bg-gray-700 focus:outline-none focus:ring-2 focus:ring-primary">
                    </div>
                </div>
                
                <div class="grid grid-cols-1 md:grid-cols-2 gap-4">
                    <div>
                        <label for="dataInternacao" class="block text-sm font-medium mb-1">Data da Internação na UTI</label>
                        <input type="date" id="dataInternacao" name="dataInternacao" required 
                            class="w-full px-3 py-2 border border-gray-300 dark:border-gray-600 rounded-md text-base
                            dark:bg-gray-700 focus:outline-none focus:ring-2 focus:ring-primary">
                    </div>
                    <div>
                        <label for="dataAlta" class="block text-sm font-medium mb-1">Data da Alta da UTI</label>
                        <input type="date" id="dataAlta" name="dataAlta" required 
                            class="w-full px-3 py-2 border border-gray-300 dark:border-gray-600 rounded-md text-base
                            dark:bg-gray-700 focus:outline-none focus:ring-2 focus:ring-primary">
                    </div>
                </div>
                
                <div class="mt-6">
                    <h2 class="text-lg md:text-xl font-semibold mb-4">Parâmetros do SWIFT Score</h2>
                    
                    <!-- Procedência do paciente -->
                    <div class="mb-4">
                        <label class="block text-sm font-medium mb-2">Procedência do paciente antes da admissão na UTI</label>
                        <div class="space-y-2">
                            <div>
                                <input type="radio" id="procedencia0" name="procedencia" value="0" required
                                    class="w-4 h-4 text-primary focus:ring-primary">
                                <label for="procedencia0" class="ml-2">Pronto-socorro (0 pontos)</label>
                            </div>
                            <div>
                                <input type="radio" id="procedencia8" name="procedencia" value="8"
                                    class="w-4 h-4 text-primary focus:ring-primary">
                                <label for="procedencia8" class="ml-2">Outro hospital (8 pontos)</label>
                            </div>
                            <div>
                                <input type="radio" id="procedencia8b" name="procedencia" value="8"
                                    class="w-4 h-4 text-primary focus:ring-primary">
                                <label for="procedencia8b" class="ml-2">Enfermaria (8 pontos)</label>
                            </div>
                        </div>
                    </div>
                    
                    <!-- Tempo de permanência na UTI -->
                    <div class="mb-4">
                        <label class="block text-sm font-medium mb-2">Tempo de permanência na UTI (em dias)</label>
                        <div class="space-y-2">
                            <div>
                                <input type="radio" id="permanencia0" name="permanencia" value="0" required
                                    class="w-4 h-4 text-primary focus:ring-primary">
                                <label for="permanencia0" class="ml-2">< 2 dias (0 pontos)</label>
                            </div>
                            <div>
                                <input type="radio" id="permanencia1" name="permanencia" value="1"
                                    class="w-4 h-4 text-primary focus:ring-primary">
                                <label for="permanencia1" class="ml-2">2-10 dias (1 ponto)</label>
                            </div>
                            <div>
                                <input type="radio" id="permanencia14" name="permanencia" value="14"
                                    class="w-4 h-4 text-primary focus:ring-primary">
                                <label for="permanencia14" class="ml-2">> 10 dias (14 pontos)</label>
                            </div>
                        </div>
                    </div>
                    
                    <!-- Última PaO₂/FiO₂ -->
                    <div class="mb-4">
                        <label class="block text-sm font-medium mb-2">Última PaO₂/FiO₂ (relação) medida antes da alta da UTI</label>
                        <div class="space-y-2">
                            <div>
                                <input type="radio" id="pao20" name="pao2" value="0" required
                                    class="w-4 h-4 text-primary focus:ring-primary">
                                <label for="pao20" class="ml-2">> 400 (0 pontos)</label>
                            </div>
                            <div>
                                <input type="radio" id="pao25" name="pao2" value="5"
                                    class="w-4 h-4 text-primary focus:ring-primary">
                                <label for="pao25" class="ml-2">< 400 e ≥ 150 (5 pontos)</label>
                            </div>
                            <div>
                                <input type="radio" id="pao210" name="pao2" value="10"
                                    class="w-4 h-4 text-primary focus:ring-primary">
                                <label for="pao210" class="ml-2">< 150 e ≥ 100 (10 pontos)</label>
                            </div>
                            <div>
                                <input type="radio" id="pao213" name="pao2" value="13"
                                    class="w-4 h-4 text-primary focus:ring-primary">
                                <label for="pao213" class="ml-2">< 100 (13 pontos)</label>
                            </div>
                        </div>
                    </div>
                    
                    <!-- Glasgow -->
                    <div class="mb-4">
                        <label class="block text-sm font-medium mb-2">Avaliação da escala de coma de Glasgow na alta da UTI</label>
                        <div class="space-y-2">
                            <div>
                                <input type="radio" id="glasgow0" name="glasgow" value="0" required
                                    class="w-4 h-4 text-primary focus:ring-primary">
                                <label for="glasgow0" class="ml-2">> 14 (0 pontos)</label>
                            </div>
                            <div>
                                <input type="radio" id="glasgow6" name="glasgow" value="6"
                                    class="w-4 h-4 text-primary focus:ring-primary">
                                <label for="glasgow6" class="ml-2">11-14 (6 pontos)</label>
                            </div>
                            <div>
                                <input type="radio" id="glasgow14" name="glasgow" value="14"
                                    class="w-4 h-4 text-primary focus:ring-primary">
                                <label for="glasgow14" class="ml-2">8-10 (14 pontos)</label>
                            </div>
                            <div>
                                <input type="radio" id="glasgow24" name="glasgow" value="24"
                                    class="w-4 h-4 text-primary focus:ring-primary">
                                <label for="glasgow24" class="ml-2">< 8 (24 pontos)</label>
                            </div>
                        </div>
                    </div>
                    
                    <!-- Última PaCO₂ -->
                    <div class="mb-4">
                        <label class="block text-sm font-medium mb-2">Última PaCO₂ medida antes da alta da UTI</label>
                        <div class="space-y-2">
                            <div>
                                <input type="radio" id="paco20" name="paco2" value="0" required
                                    class="w-4 h-4 text-primary focus:ring-primary">
                                <label for="paco20" class="ml-2">< 45 mmHg (0 pontos)</label>
                            </div>
                            <div>
                                <input type="radio" id="paco25" name="paco2" value="5"
                                    class="w-4 h-4 text-primary focus:ring-primary">
                                <label for="paco25" class="ml-2">≥ 45 mmHg (5 pontos)</label>
                            </div>
                        </div>
                    </div>
                    
                    <div class="p-4 bg-gray-100 dark:bg-gray-700 rounded-md mb-4">
                        <div class="flex flex-col md:flex-row justify-between items-start md:items-center gap-2">
                            <span class="font-medium">SWIFT Score Final:</span>
                            <div class="flex flex-col items-end">
                                <span id="scoreFinal" class="text-xl font-bold">0</span>
                                <span id="riskLevel" class="text-sm font-medium">Risco baixo</span>
                            </div>
                        </div>
                    </div>
                </div>
                
                <div class="flex flex-col md:flex-row gap-3 pt-4">
                    <button type="submit" 
                        class="px-4 py-2 bg-primary text-white rounded-md hover:bg-primary-dark focus:outline-none focus:ring-2 focus:ring-primary focus:ring-offset-2">
                        Registrar Paciente
                    </button>
                    <button type="button" id="exportBtn"
                        class="px-4 py-2 bg-green-600 text-white rounded-md hover:bg-green-700 focus:outline-none focus:ring-2 focus:ring-green-600 focus:ring-offset-2">
                        Exportar para CSV
                    </button>
                    <label for="importFile" 
                        class="px-4 py-2 bg-blue-600 text-white rounded-md hover:bg-blue-700 focus:outline-none focus:ring-2 focus:ring-blue-600 focus:ring-offset-2 cursor-pointer text-center">
                        Importar CSV
                    </label>
                    <input type="file" id="importFile" accept=".csv" class="hidden">
                </div>
            </form>
        </div>
        
        <!-- Tabela de Pacientes -->
        <div class="bg-white dark:bg-gray-800 rounded-lg shadow-md p-4 md:p-6">
            <h2 class="text-lg md:text-xl font-semibold mb-4">Pacientes Registrados</h2>
            <div class="overflow-x-auto">
                <table class="min-w-full divide-y divide-gray-200 dark:divide-gray-700">
                    <thead class="bg-gray-50 dark:bg-gray-700">
                        <tr>
                            <th class="px-4 py-3 text-left text-xs font-medium text-gray-500 dark:text-gray-300 uppercase tracking-wider">Nome</th>
                            <th class="px-4 py-3 text-left text-xs font-medium text-gray-500 dark:text-gray-300 uppercase tracking-wider">Registro</th>
                            <th class="px-4 py-3 text-left text-xs font-medium text-gray-500 dark:text-gray-300 uppercase tracking-wider">Score</th>
                            <th class="px-4 py-3 text-left text-xs font-medium text-gray-500 dark:text-gray-300 uppercase tracking-wider">Risco</th>
                        </tr>
                    </thead>
                    <tbody id="patientTableBody" class="bg-white dark:bg-gray-800 divide-y divide-gray-200 dark:divide-gray-700">
                        <tr>
                            <td colspan="4" class="px-4 py-4 text-center text-sm text-gray-500 dark:text-gray-400">
                                Nenhum paciente registrado
                            </td>
                        </tr>
                    </tbody>
                </table>
            </div>
        </div>
        
        <!-- Modal de Informações do Score -->
        <div id="infoModal" class="fixed inset-0 bg-black bg-opacity-50 z-50 flex items-center justify-center hidden">
            <div class="bg-white dark:bg-gray-800 rounded-lg shadow-xl p-4 md:p-6 max-w-2xl w-full max-h-[90vh] overflow-y-auto mx-4">
                <div class="flex justify-between items-center mb-4">
                    <h3 class="text-xl font-bold text-primary dark:text-primary">Sobre o SWIFT Score</h3>
                    <button id="closeModal" class="text-gray-500 hover:text-gray-700 dark:text-gray-400 dark:hover:text-gray-200 focus:outline-none">
                        <svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12" />
                        </svg>
                    </button>
                </div>
                
                <div class="space-y-6">
                    <div>
                        <h4 class="text-lg font-semibold mb-2">O que é o SWIFT Score?</h4>
                        <p class="text-sm">O SWIFT (Stability and Workload Index For Transfer) é um instrumento para avaliar o risco de readmissão na UTI. Foi desenvolvido para prever quais pacientes têm maior probabilidade de precisar retornar à UTI após receberem alta.</p>
                    </div>
                    
                    <div>
                        <h4 class="text-lg font-semibold mb-2">Como preencher o formulário</h4>
                        <ul class="list-disc pl-5 space-y-2 text-sm">
                            <li>Preencha os dados do paciente (nome, registro e datas)</li>
                            <li>Selecione as opções adequadas para cada parâmetro do SWIFT Score</li>
                            <li>O score final será calculado automaticamente</li>
                            <li>Clique em "Registrar Paciente" para adicionar à lista</li>
                        </ul>
                    </div>
                    
                    <div>
                        <h4 class="text-lg font-semibold mb-2">Componentes do SWIFT Score</h4>
                        
                        <div class="space-y-4">
                            <div class="bg-blue-50 dark:bg-blue-900/30 p-3 rounded-md">
                                <h5 class="font-medium mb-1">Procedência do paciente antes da admissão na UTI</h5>
                                <ul class="list-disc pl-5 text-sm">
                                    <li>Pronto-socorro: 0 pontos</li>
                                    <li>Outro hospital: 8 pontos</li>
                                    <li>Enfermaria: 8 pontos</li>
                                </ul>
                            </div>
                            
                            <div class="bg-blue-50 dark:bg-blue-900/30 p-3 rounded-md">
                                <h5 class="font-medium mb-1">Tempo de permanência na UTI (em dias)</h5>
                                <ul class="list-disc pl-5 text-sm">
                                    <li>&lt; 2 dias: 0 pontos</li>
                                    <li>2-10 dias: 1 ponto</li>
                                    <li>&gt; 10 dias: 14 pontos</li>
                                </ul>
                            </div>
                            
                            <div class="bg-blue-50 dark:bg-blue-900/30 p-3 rounded-md">
                                <h5 class="font-medium mb-1">Última PaO₂/FiO₂ medida antes da alta da UTI</h5>
                                <ul class="list-disc pl-5 text-sm">
                                    <li>&gt; 400: 0 pontos</li>
                                    <li>&lt; 400 e ≥ 150: 5 pontos</li>
                                    <li>&lt; 150 e ≥ 100: 10 pontos</li>
                                    <li>&lt; 100: 13 pontos</li>
                                </ul>
                            </div>
                            
                            <div class="bg-blue-50 dark:bg-blue-900/30 p-3 rounded-md">
                                <h5 class="font-medium mb-1">Avaliação da escala de coma de Glasgow na alta da UTI</h5>
                                <ul class="list-disc pl-5 text-sm">
                                    <li>&gt; 14: 0 pontos</li>
                                    <li>11-14: 6 pontos</li>
                                    <li>8-10: 14 pontos</li>
                                    <li>&lt; 8: 24 pontos</li>
                                </ul>
                            </div>
                            
                            <div class="bg-blue-50 dark:bg-blue-900/30 p-3 rounded-md">
                                <h5 class="font-medium mb-1">Última PaCO₂ medida antes da alta da UTI</h5>
                                <ul class="list-disc pl-5 text-sm">
                                    <li>&lt; 45 mmHg: 0 pontos</li>
                                    <li>≥ 45 mmHg: 5 pontos</li>
                                </ul>
                            </div>
                        </div>
                    </div>
                    
                    <div>
                        <h4 class="text-lg font-semibold mb-2">Interpretação do Score</h4>
                        <ul class="text-sm space-y-2">
                            <li><span class="inline-block w-4 h-4 bg-green-500 rounded-full mr-2"></span><strong>0-6 pontos:</strong> Baixo risco de readmissão na UTI</li>
                            <li><span class="inline-block w-4 h-4 bg-yellow-500 rounded-full mr-2"></span><strong>7-14 pontos:</strong> Risco moderado de readmissão</li>
                            <li><span class="inline-block w-4 h-4 bg-orange-500 rounded-full mr-2"></span><strong>15-30 pontos:</strong> Alto risco de readmissão</li>
                            <li><span class="inline-block w-4 h-4 bg-red-500 rounded-full mr-2"></span><strong>&gt; 30 pontos:</strong> Risco muito alto de readmissão</li>
                        </ul>
                        <p class="mt-2 text-sm italic">O SWIFT Score varia de 0 a 59 pontos. Quanto maior o score, maior o risco de readmissão na UTI.</p>
                    </div>
                </div>
            </div>
        </div>

    </div>

    <script>
        document.addEventListener('DOMContentLoaded', function() {
            // Arrays para armazenar dados de pacientes
            let patients = [];
            
            // Elementos do DOM
            const form = document.getElementById('swiftForm');
            const scoreFinalEl = document.getElementById('scoreFinal');
            const riskLevelEl = document.getElementById('riskLevel');
            const tableBody = document.getElementById('patientTableBody');
            const exportBtn = document.getElementById('exportBtn');
            const importFile = document.getElementById('importFile');
            
            // Elementos do modal de informações
            const infoBtn = document.getElementById('infoBtn');
            const infoModal = document.getElementById('infoModal');
            const closeModal = document.getElementById('closeModal');
            
            // Inputs do score
            const procedenciaInputs = document.querySelectorAll('input[name="procedencia"]');
            const permanenciaInputs = document.querySelectorAll('input[name="permanencia"]');
            const pao2Inputs = document.querySelectorAll('input[name="pao2"]');
            const glasgowInputs = document.querySelectorAll('input[name="glasgow"]');
            const paco2Inputs = document.querySelectorAll('input[name="paco2"]');
            
            // Abrir modal de informações
            infoBtn.addEventListener('click', function() {
                infoModal.classList.remove('hidden');
                document.body.style.overflow = 'hidden'; // Prevenir scroll do body
            });
            
            // Fechar modal de informações
            closeModal.addEventListener('click', function() {
                infoModal.classList.add('hidden');
                document.body.style.overflow = ''; // Restaurar scroll
            });
            
            // Fechar modal ao clicar fora da janela de informações
            infoModal.addEventListener('click', function(e) {
                if (e.target === infoModal) {
                    infoModal.classList.add('hidden');
                    document.body.style.overflow = '';
                }
            });
            
            // Fechar modal ao pressionar ESC
            document.addEventListener('keydown', function(e) {
                if (e.key === 'Escape' && !infoModal.classList.contains('hidden')) {
                    infoModal.classList.add('hidden');
                    document.body.style.overflow = '';
                }
            });
            
            // Calcular score
            function calculateScore() {
                let score = 0;
                
                // Procedência
                const procedencia = document.querySelector('input[name="procedencia"]:checked');
                if (procedencia) score += parseInt(procedencia.value);
                
                // Permanência
                const permanencia = document.querySelector('input[name="permanencia"]:checked');
                if (permanencia) score += parseInt(permanencia.value);
                
                // PaO2/FiO2
                const pao2 = document.querySelector('input[name="pao2"]:checked');
                if (pao2) score += parseInt(pao2.value);
                
                // Glasgow
                const glasgow = document.querySelector('input[name="glasgow"]:checked');
                if (glasgow) score += parseInt(glasgow.value);
                
                // PaCO2
                const paco2 = document.querySelector('input[name="paco2"]:checked');
                if (paco2) score += parseInt(paco2.value);
                
                scoreFinalEl.textContent = score;
                
                // Determinar nível de risco
                let riskText = '';
                let riskClass = '';
                
                if (score <= 6) {
                    riskText = 'Risco baixo';
                    riskClass = 'text-green-600 dark:text-green-400';
                } else if (score <= 14) {
                    riskText = 'Risco moderado';
                    riskClass = 'text-yellow-600 dark:text-yellow-400';
                } else if (score <= 30) {
                    riskText = 'Risco alto';
                    riskClass = 'text-orange-600 dark:text-orange-400';
                } else {
                    riskText = 'Risco muito alto';
                    riskClass = 'text-red-600 dark:text-red-400';
                }
                
                riskLevelEl.textContent = riskText;
                riskLevelEl.className = 'text-sm font-medium ' + riskClass;
                
                return score;
            }
            
            // Atualizar score ao selecionar qualquer opção
            const allInputs = [
                ...procedenciaInputs, 
                ...permanenciaInputs, 
                ...pao2Inputs, 
                ...glasgowInputs, 
                ...paco2Inputs
            ];
            
            allInputs.forEach(input => {
                input.addEventListener('change', calculateScore);
            });
            
            // Submeter formulário
            form.addEventListener('submit', function(e) {
                e.preventDefault();
                
                // Verificar se todos os campos obrigatórios foram preenchidos
                const requiredGroups = ['procedencia', 'permanencia', 'pao2', 'glasgow', 'paco2'];
                let allValid = true;
                
                for (let group of requiredGroups) {
                    if (!document.querySelector(`input[name="${group}"]:checked`)) {
                        alert(`Por favor, selecione uma opção para ${group.charAt(0).toUpperCase() + group.slice(1)}`);
                        allValid = false;
                        break;
                    }
                }
                
                if (!allValid) return;
                
                // Calcular score final
                const finalScore = calculateScore();
                
                // Determinar nível de risco
                let riskText = '';
                
                if (finalScore <= 6) {
                    riskText = 'Baixo';
                } else if (finalScore <= 14) {
                    riskText = 'Moderado';
                } else if (finalScore <= 30) {
                    riskText = 'Alto';
                } else {
                    riskText = 'Muito alto';
                }
                
                // Criar objeto do paciente
                const patient = {
                    nome: document.getElementById('nome').value,
                    registro: document.getElementById('registro').value,
                    dataInternacao: document.getElementById('dataInternacao').value,
                    dataAlta: document.getElementById('dataAlta').value,
                    procedencia: document.querySelector('input[name="procedencia"]:checked').value,
                    permanencia: document.querySelector('input[name="permanencia"]:checked').value,
                    pao2: document.querySelector('input[name="pao2"]:checked').value,
                    glasgow: document.querySelector('input[name="glasgow"]:checked').value,
                    paco2: document.querySelector('input[name="paco2"]:checked').value,
                    score: finalScore,
                    risco: riskText
                };
                
                // Adicionar à lista e atualizar tabela
                patients.push(patient);
                updateTable();
                
                // Limpar formulário
                form.reset();
                scoreFinalEl.textContent = "0";
                riskLevelEl.textContent = "Risco baixo";
                riskLevelEl.className = "text-sm font-medium text-green-600 dark:text-green-400";
                
                // Feedback ao usuário
                alert("Paciente registrado com sucesso!");
            });
            
            // Exportar para CSV
            exportBtn.addEventListener('click', function() {
                if (patients.length === 0) {
                    alert("Não há pacientes para exportar.");
                    return;
                }
                
                // Criar cabeçalho do CSV
                let csv = 'Nome,Registro,Data Internação,Data Alta,Procedência,Permanência,PaO2/FiO2,Glasgow,PaCO2,Score,Risco\n';
                
                // Adicionar cada paciente
                patients.forEach(patient => {
                    csv += `"${patient.nome}","${patient.registro}","${patient.dataInternacao}","${patient.dataAlta}",` +
                           `"${patient.procedencia}","${patient.permanencia}","${patient.pao2}","${patient.glasgow}",` +
                           `"${patient.paco2}","${patient.score}","${patient.risco}"\n`;
                });
                
                // Criar e baixar o arquivo
                const blob = new Blob([csv], { type: 'text/csv;charset=utf-8;' });
                const url = URL.createObjectURL(blob);
                const link = document.createElement('a');
                link.setAttribute('href', url);
                link.setAttribute('download', 'swift_score_' + new Date().toISOString().substring(0, 10) + '.csv');
                link.style.visibility = 'hidden';
                document.body.appendChild(link);
                link.click();
                document.body.removeChild(link);
            });
            
            // Importar CSV
            importFile.addEventListener('change', function(e) {
                const file = e.target.files[0];
                if (!file) return;
                
                const reader = new FileReader();
                reader.onload = function(e) {
                    try {
                        const contents = e.target.result;
                        const rows = contents.split('\n');
                        
                        // Pular cabeçalho
                        for (let i = 1; i < rows.length; i++) {
                            if (rows[i].trim() === '') continue;
                            
                            // Tratar campos com vírgulas dentro de aspas
                            let fields = [];
                            let field = '';
                            let inQuotes = false;
                            
                            for (let j = 0; j < rows[i].length; j++) {
                                const char = rows[i][j];
                                
                                if (char === '"') {
                                    inQuotes = !inQuotes;
                                } else if (char === ',' && !inQuotes) {
                                    fields.push(field);
                                    field = '';
                                } else {
                                    field += char;
                                }
                            }
                            
                            // Adicionar último campo
                            fields.push(field);
                            
                            // Remover aspas extras
                            fields = fields.map(f => f.replace(/^"|"$/g, ''));
                            
                            if (fields.length >= 11) {
                                patients.push({
                                    nome: fields[0],
                                    registro: fields[1],
                                    dataInternacao: fields[2],
                                    dataAlta: fields[3],
                                    procedencia: fields[4],
                                    permanencia: fields[5],
                                    pao2: fields[6],
                                    glasgow: fields[7],
                                    paco2: fields[8],
                                    score: parseInt(fields[9]),
                                    risco: fields[10]
                                });
                            }
                        }
                        
                        updateTable();
                        alert(`CSV importado com sucesso. Total de pacientes: ${patients.length}`);
                    } catch (error) {
                        console.error("Erro ao importar CSV:", error);
                        alert("Erro ao importar o arquivo CSV. Verifique o formato do arquivo.");
                    }
                };
                reader.readAsText(file);
            });
            
            // Atualizar tabela de pacientes
            function updateTable() {
                if (patients.length === 0) {
                    tableBody.innerHTML = `
                        <tr>
                            <td colspan="4" class="px-4 py-4 text-center text-sm text-gray-500 dark:text-gray-400">
                                Nenhum paciente registrado
                            </td>
                        </tr>
                    `;
                    return;
                }
                
                tableBody.innerHTML = '';
                patients.forEach(patient => {
                    // Formatação das datas para exibição
                    const formatDate = (dateStr) => {
                        const [year, month, day] = dateStr.split('-');
                        return `${day}/${month}/${year}`;
                    };
                    
                    // Cor baseada no risco
                    let riskColorClass = '';
                    switch(patient.risco) {
                        case 'Baixo': riskColorClass = 'bg-green-100 text-green-800 dark:bg-green-800 dark:text-green-100'; break;
                        case 'Moderado': riskColorClass = 'bg-yellow-100 text-yellow-800 dark:bg-yellow-800 dark:text-yellow-100'; break;
                        case 'Alto': riskColorClass = 'bg-orange-100 text-orange-800 dark:bg-orange-800 dark:text-orange-100'; break;
                        case 'Muito alto': riskColorClass = 'bg-red-100 text-red-800 dark:bg-red-800 dark:text-red-100'; break;
                    }
                    
                    const row = document.createElement('tr');
                    row.classList.add('hover:bg-gray-50', 'dark:hover:bg-gray-700');
                    row.innerHTML = `
                        <td class="px-4 py-4 whitespace-nowrap text-sm">${patient.nome}</td>
                        <td class="px-4 py-4 whitespace-nowrap text-sm">${patient.registro}</td>
                        <td class="px-4 py-4 whitespace-nowrap text-sm">${patient.score}</td>
                        <td class="px-4 py-4 whitespace-nowrap text-sm">
                            <span class="inline-flex items-center px-2.5 py-0.5 rounded-full text-xs font-medium ${riskColorClass}">
                                ${patient.risco}
                            </span>
                        </td>
                    `;
                    tableBody.appendChild(row);
                });
            }
        });
    </script>
</body>
</html>

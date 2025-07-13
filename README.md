<html><head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <script src="https://cdn.tailwindcss.com"></script>
    <script src="https://code.highcharts.com/highcharts.js"></script>
    <script> window.FontAwesomeConfig = { autoReplaceSvg: 'nest'};</script>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/js/all.min.js" crossorigin="anonymous" referrerpolicy="no-referrer"></script>
    
    <style>
        ::-webkit-scrollbar { display: none;}
        body { font-family: 'Inter', sans-serif; }
        .bg-blue-bic { background-color: #1e3a8a; }
        .text-blue-bic { color: #1e3a8a; }
        .border-blue-bic { border-color: #1e3a8a; }
    </style>
    <script>tailwind.config = {
  "theme": {
    "extend": {
      "colors": {
        "blue-bic": "#1e3a8a"
      },
      "fontFamily": {
        "sans": [
          "Inter",
          "sans-serif"
        ]
      }
    }
  }
};</script>
<link rel="preconnect" href="https://fonts.googleapis.com"><link rel="preconnect" href="https://fonts.gstatic.com" crossorigin=""><link rel="stylesheet" href="https://fonts.googleapis.com/css2?family=Inter:wght@100;200;300;500;600;700;800;900&amp;display=swap"><style>
  .highlighted-section {
    outline: 2px solid #3F20FB;
    background-color: rgba(63, 32, 251, 0.1);
  }

  .edit-button {
    position: absolute;
    z-index: 1000;
  }

  ::-webkit-scrollbar {
    display: none;
  }

  html, body {
    -ms-overflow-style: none;
    scrollbar-width: none;
  }
  </style></head>
<body class="bg-gray-50">

<!-- Sidebar -->
<div id="sidebar" class="fixed left-0 top-0 h-full w-64 bg-blue-bic text-white z-50">
    <div class="p-6">
        <h1 class="text-xl font-bold">UNS Admin</h1>
        <p class="text-blue-200 text-sm">Université Numérique du Sénégal</p>
    </div>
    
    <nav class="mt-8">
        <span class="flex items-center px-6 py-3 bg-blue-700 border-r-4 border-white cursor-pointer">
            <i class="fa-solid fa-chart-line mr-3"></i>
            <span>Tableau de Bord</span>
        </span>
        <span class="flex items-center px-6 py-3 hover:bg-blue-700 transition-colors cursor-pointer">
            <i class="fa-solid fa-users mr-3"></i>
            <span>Gestion Responsables</span>
        </span>
        <span class="flex items-center px-6 py-3 hover:bg-blue-700 transition-colors cursor-pointer">
            <i class="fa-solid fa-chalkboard-teacher mr-3"></i>
            <span>Gestion Enseignants</span>
        </span>
        <span class="flex items-center px-6 py-3 hover:bg-blue-700 transition-colors cursor-pointer">
            <i class="fa-solid fa-user-graduate mr-3"></i>
            <span>Gestion Étudiants</span>
        </span>
        <span class="flex items-center px-6 py-3 hover:bg-blue-700 transition-colors cursor-pointer">
            <i class="fa-solid fa-graduation-cap mr-3"></i>
            <span>Gestion Filières</span>
        </span>
        <span class="flex items-center px-6 py-3 hover:bg-blue-700 transition-colors cursor-pointer">
            <i class="fa-solid fa-clipboard-check mr-3"></i>
            <span>Délibérations</span>
        </span>
    </nav>
</div>

<!-- Main Content -->
<div id="main-content" class="ml-64">
    <!-- Header -->
    <header id="header" class="bg-white shadow-sm border-b px-6 py-4">
        <div class="flex justify-between items-center">
            <div>
                <h2 class="text-2xl font-bold text-blue-bic">Tableau de Bord</h2>
                <p class="text-gray-600">Vue d'ensemble de l'université</p>
            </div>
            <div class="flex items-center space-x-4">
                <div class="relative">
                    <i class="fa-solid fa-bell text-gray-400 text-xl"></i>
                    <span class="absolute -top-1 -right-1 bg-red-500 text-white text-xs rounded-full h-5 w-5 flex items-center justify-center">3</span>
                </div>
                <img src="https://storage.googleapis.com/uxpilot-auth.appspot.com/avatars/avatar-2.jpg" alt="Admin" class="w-10 h-10 rounded-full">
            </div>
        </div>
    </header>

    <!-- Dashboard Content -->
    <div id="dashboard-content" class="p-6">
        
        <!-- Partie 1: Statistiques Académiques -->
        <div id="academic-stats" class="mb-8">
            <h3 class="text-xl font-semibold text-blue-bic mb-6">Statistiques Académiques</h3>
            
            <!-- Taux de Réussite/Échec -->
            <div class="grid grid-cols-1 lg:grid-cols-2 gap-6 mb-6">
                <div id="success-rate-card" class="bg-white rounded-lg shadow-sm p-6">
                    <h4 class="text-lg font-medium text-blue-bic mb-4">Taux de Réussite par Filière</h4>
                    <div id="successChart" class="h-80"></div>
                </div>
                
                <div id="failure-rate-card" class="bg-white rounded-lg shadow-sm p-6">
                    <h4 class="text-lg font-medium text-blue-bic mb-4">Taux d'Échec par Niveau</h4>
                    <div id="failureChart" class="h-80"></div>
                </div>
            </div>

            <!-- Effectifs -->
            <div class="grid grid-cols-1 lg:grid-cols-2 gap-6">
                <div id="students-count-card" class="bg-white rounded-lg shadow-sm p-6">
                    <h4 class="text-lg font-medium text-blue-bic mb-4">Nombre d'Étudiants par Filière</h4>
                    <div id="studentsChart" class="h-80"></div>
                </div>
                
                <div id="teachers-count-card" class="bg-white rounded-lg shadow-sm p-6">
                    <h4 class="text-lg font-medium text-blue-bic mb-4">Enseignants et Responsables</h4>
                    <div id="teachersChart" class="h-80"></div>
                </div>
            </div>
        </div>

        <!-- Partie 2: Alertes et Insertion -->
        <div id="alerts-insertion" class="mb-8">
            <h3 class="text-xl font-semibold text-blue-bic mb-6">Alertes et Insertion Professionnelle</h3>
            
            <div class="grid grid-cols-1 lg:grid-cols-2 gap-6">
                <!-- Alertes -->
                <div id="alerts-card" class="bg-white rounded-lg shadow-sm p-6">
                    <h4 class="text-lg font-medium text-red-600 mb-4">
                        <i class="fa-solid fa-exclamation-triangle mr-2"></i>
                        Alertes Système
                    </h4>
                    <div class="space-y-4">
                        <div class="flex items-center p-3 bg-red-50 rounded-lg border-l-4 border-red-500">
                            <i class="fa-solid fa-user-times text-red-500 mr-3"></i>
                            <div>
                                <p class="font-medium text-red-800">12 Enseignants non affectés</p>
                                <p class="text-red-600 text-sm">Nécessite une affectation urgente</p>
                            </div>
                        </div>
                        
                        <div class="flex items-center p-3 bg-yellow-50 rounded-lg border-l-4 border-yellow-500">
                            <i class="fa-solid fa-user-graduate text-yellow-500 mr-3"></i>
                            <div>
                                <p class="font-medium text-yellow-800">8 Étudiants sans filière</p>
                                <p class="text-yellow-600 text-sm">Orientation en attente</p>
                            </div>
                        </div>
                        
                        <div class="flex items-center p-3 bg-orange-50 rounded-lg border-l-4 border-orange-500">
                            <i class="fa-solid fa-calendar-times text-orange-500 mr-3"></i>
                            <div>
                                <p class="font-medium text-orange-800">3 Cours sans enseignant</p>
                                <p class="text-orange-600 text-sm">Filière MIC - Niveau M1</p>
                            </div>
                        </div>
                    </div>
                </div>

                <!-- Taux d'Insertion -->
                <div id="insertion-rate-card" class="bg-white rounded-lg shadow-sm p-6">
                    <h4 class="text-lg font-medium text-blue-bic mb-4">Taux d'Insertion Professionnelle</h4>
                    <div id="insertionChart" class="h-80"></div>
                </div>
            </div>
        </div>

        <!-- Résumé Rapide -->
        <div id="quick-summary" class="grid grid-cols-1 md:grid-cols-4 gap-4">
            <div class="bg-blue-bic text-white p-6 rounded-lg">
                <div class="flex items-center justify-between">
                    <div>
                        <p class="text-blue-200">Total Étudiants</p>
                        <p class="text-2xl font-bold">2,847</p>
                    </div>
                    <i class="fa-solid fa-users text-3xl text-blue-300"></i>
                </div>
            </div>
            
            <div class="bg-green-600 text-white p-6 rounded-lg">
                <div class="flex items-center justify-between">
                    <div>
                        <p class="text-green-200">Enseignants</p>
                        <p class="text-2xl font-bold">156</p>
                    </div>
                    <i class="fa-solid fa-chalkboard-teacher text-3xl text-green-300"></i>
                </div>
            </div>
            
            <div class="bg-purple-600 text-white p-6 rounded-lg">
                <div class="flex items-center justify-between">
                    <div>
                        <p class="text-purple-200">Filières</p>
                        <p class="text-2xl font-bold">3</p>
                    </div>
                    <i class="fa-solid fa-graduation-cap text-3xl text-purple-300"></i>
                </div>
            </div>
            
            <div class="bg-orange-600 text-white p-6 rounded-lg">
                <div class="flex items-center justify-between">
                    <div>
                        <p class="text-orange-200">Taux Réussite</p>
                        <p class="text-2xl font-bold">78%</p>
                    </div>
                    <i class="fa-solid fa-chart-line text-3xl text-orange-300"></i>
                </div>
            </div>
        </div>
    </div>
</div>

<script>
// Taux de Réussite par Filière
Highcharts.chart('successChart', {
    chart: { type: 'column' },
    title: { text: null },
    xAxis: { categories: ['MIC', 'IDA', 'CD'] },
    yAxis: { title: { text: 'Taux (%)' }, max: 100 },
    series: [{
        name: 'L1', data: [75, 82, 78], color: '#1e3a8a'
    }, {
        name: 'L2', data: [80, 76, 85], color: '#3b82f6'
    }, {
        name: 'L3', data: [85, 88, 82], color: '#60a5fa'
    }, {
        name: 'M1', data: [90, 85, 88], color: '#93c5fd'
    }, {
        name: 'M2', data: [92, 89, 91], color: '#bfdbfe'
    }]
});

// Taux d'Échec par Niveau
Highcharts.chart('failureChart', {
    chart: { type: 'pie' },
    title: { text: null },
    series: [{
        data: [
            { name: 'L1', y: 25, color: '#dc2626' },
            { name: 'L2', y: 20, color: '#ef4444' },
            { name: 'L3', y: 15, color: '#f87171' },
            { name: 'M1', y: 10, color: '#fca5a5' },
            { name: 'M2', y: 8, color: '#fecaca' }
        ]
    }]
});

// Nombre d'Étudiants par Filière
Highcharts.chart('studentsChart', {
    chart: { type: 'bar' },
    title: { text: null },
    xAxis: { categories: ['L1', 'L2', 'L3', 'M1', 'M2'] },
    yAxis: { title: { text: 'Nombre d\'étudiants' } },
    series: [{
        name: 'MIC', data: [450, 380, 320, 180, 120], color: '#1e3a8a'
    }, {
        name: 'IDA', data: [420, 350, 290, 160, 110], color: '#3b82f6'
    }, {
        name: 'CD', data: [380, 320, 270, 140, 95], color: '#60a5fa'
    }]
});

// Enseignants et Responsables
Highcharts.chart('teachersChart', {
    chart: { type: 'column' },
    title: { text: null },
    xAxis: { categories: ['MIC', 'IDA', 'CD'] },
    yAxis: { title: { text: 'Nombre' } },
    series: [{
        name: 'Enseignants', data: [52, 48, 56], color: '#1e3a8a'
    }, {
        name: 'Responsables', data: [3, 3, 3], color: '#ef4444'
    }]
});

// Taux d'Insertion Professionnelle
Highcharts.chart('insertionChart', {
    chart: { type: 'line' },
    title: { text: null },
    xAxis: { categories: ['2019', '2020', '2021', '2022', '2023'] },
    yAxis: { title: { text: 'Taux d\'insertion (%)' }, max: 100 },
    series: [{
        name: 'MIC', data: [78, 82, 85, 88, 92], color: '#1e3a8a'
    }, {
        name: 'IDA', data: [75, 79, 83, 86, 89], color: '#3b82f6'
    }, {
        name: 'CD', data: [72, 76, 80, 84, 87], color: '#60a5fa'
    }]
});
</script>


</body></html>

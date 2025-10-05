<!DOCTYPE html>
<html lang="ru">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Портфолио проектов | GitHub + Диплом</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }

        :root {
            --primary: #6c5ce7;
            --secondary: #a29bfe;
            --dark: #2d3436;
            --light: #f5f6fa;
            --success: #00b894;
            --warning: #fdcb6e;
            --danger: #e17055;
            --github: #333;
        }

        body {
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            color: var(--dark);
            line-height: 1.6;
            min-height: 100vh;
        }

        .container {
            max-width: 1400px;
            margin: 0 auto;
            padding: 20px;
        }

        header {
            background: rgba(255, 255, 255, 0.95);
            border-radius: 20px;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.1);
            padding: 30px;
            margin-bottom: 30px;
            backdrop-filter: blur(10px);
        }

        h1 {
            font-size: 2.8rem;
            margin-bottom: 10px;
            background: linear-gradient(135deg, var(--primary), var(--secondary));
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            text-align: center;
        }

        .subtitle {
            font-size: 1.2rem;
            color: #636e72;
            margin-bottom: 20px;
            text-align: center;
        }

        .controls {
            display: flex;
            justify-content: space-between;
            align-items: center;
            flex-wrap: wrap;
            gap: 20px;
            margin-top: 20px;
        }

        .search-container {
            flex: 1;
            min-width: 300px;
            position: relative;
        }

        #search {
            width: 100%;
            padding: 15px 20px;
            border: 2px solid #ddd;
            border-radius: 50px;
            font-size: 1.1rem;
            transition: all 0.3s ease;
        }

        #search:focus {
            border-color: var(--primary);
            box-shadow: 0 0 0 3px rgba(108, 92, 231, 0.2);
            outline: none;
        }

        .filters {
            display: flex;
            flex-wrap: wrap;
            gap: 10px;
        }

        .filter-btn {
            padding: 10px 20px;
            background: white;
            border: 2px solid #ddd;
            border-radius: 50px;
            cursor: pointer;
            transition: all 0.3s ease;
            font-weight: 500;
        }

        .filter-btn.active, .filter-btn:hover {
            background: var(--primary);
            color: white;
            border-color: var(--primary);
        }

        .github-setup {
            background: rgba(255, 255, 255, 0.9);
            border-radius: 15px;
            padding: 20px;
            margin-bottom: 20px;
            border-left: 5px solid var(--github);
        }

        .setup-form {
            display: flex;
            gap: 15px;
            flex-wrap: wrap;
            align-items: center;
        }

        .setup-form input {
            padding: 12px 15px;
            border: 2px solid #ddd;
            border-radius: 8px;
            font-size: 1rem;
            flex: 1;
            min-width: 250px;
        }

        .setup-form button {
            padding: 12px 25px;
            background: var(--github);
            color: white;
            border: none;
            border-radius: 8px;
            cursor: pointer;
            font-weight: 500;
            transition: all 0.3s ease;
        }

        .setup-form button:hover {
            background: #555;
        }

        .main-content {
            display: grid;
            grid-template-columns: 1fr 350px;
            gap: 30px;
        }

        @media (max-width: 1100px) {
            .main-content {
                grid-template-columns: 1fr;
            }
        }

        .projects-section {
            background: rgba(255, 255, 255, 0.95);
            border-radius: 20px;
            padding: 25px;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.1);
            backdrop-filter: blur(10px);
        }

        .diploma-section {
            background: rgba(255, 255, 255, 0.95);
            border-radius: 20px;
            padding: 25px;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.1);
            backdrop-filter: blur(10px);
            height: fit-content;
            position: sticky;
            top: 20px;
        }

        .section-title {
            font-size: 1.5rem;
            margin-bottom: 20px;
            color: var(--dark);
            display: flex;
            align-items: center;
            gap: 10px;
        }

        .section-title i {
            color: var(--primary);
        }

        .projects-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(320px, 1fr));
            gap: 25px;
        }

        .project-card {
            background: white;
            border-radius: 15px;
            overflow: hidden;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.08);
            transition: all 0.3s ease;
            border: 1px solid #eee;
        }

        .project-card:hover {
            transform: translateY(-5px);
            box-shadow: 0 10px 25px rgba(0, 0, 0, 0.15);
        }

        .project-header {
            padding: 20px;
            border-bottom: 1px solid #eee;
            display: flex;
            justify-content: between;
            align-items: flex-start;
        }

        .project-title {
            font-size: 1.3rem;
            margin-bottom: 5px;
            color: var(--dark);
            flex: 1;
        }

        .project-actions {
            display: flex;
            gap: 10px;
        }

        .action-btn {
            background: none;
            border: none;
            font-size: 1.2rem;
            cursor: pointer;
            transition: all 0.3s ease;
            width: 35px;
            height: 35px;
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
        }

        .add-to-diploma {
            color: var(--success);
        }

        .add-to-diploma:hover {
            background: rgba(0, 184, 148, 0.1);
        }

        .github-link {
            color: var(--github);
        }

        .github-link:hover {
            background: rgba(51, 51, 51, 0.1);
        }

        .project-description {
            padding: 0 20px;
            color: #636e72;
            margin-bottom: 15px;
            height: 60px;
            overflow: hidden;
        }

        .project-meta {
            padding: 0 20px;
            display: flex;
            justify-content: space-between;
            color: #636e72;
            font-size: 0.9rem;
            margin-bottom: 15px;
        }

        .project-tech {
            display: flex;
            flex-wrap: wrap;
            gap: 8px;
            padding: 0 20px 20px;
        }

        .tech-tag {
            background: #e9ecef;
            padding: 5px 12px;
            border-radius: 50px;
            font-size: 0.85rem;
            color: #495057;
        }

        .diploma-list {
            max-height: 500px;
            overflow-y: auto;
        }

        .diploma-item {
            background: white;
            border-radius: 10px;
            padding: 15px;
            margin-bottom: 15px;
            box-shadow: 0 3px 10px rgba(0, 0, 0, 0.08);
            display: flex;
            justify-content: space-between;
            align-items: center;
        }

        .diploma-item-info h4 {
            margin-bottom: 5px;
            color: var(--dark);
        }

        .diploma-item-info p {
            color: #636e72;
            font-size: 0.9rem;
        }

        .remove-btn {
            background: none;
            border: none;
            color: var(--danger);
            cursor: pointer;
            font-size: 1.2rem;
            width: 35px;
            height: 35px;
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            transition: all 0.3s ease;
        }

        .remove-btn:hover {
            background: rgba(225, 112, 85, 0.1);
        }

        .export-actions {
            margin-top: 20px;
            display: flex;
            gap: 10px;
        }

        .export-btn {
            padding: 12px 20px;
            border: none;
            border-radius: 8px;
            cursor: pointer;
            font-weight: 500;
            transition: all 0.3s ease;
            flex: 1;
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 8px;
        }

        .export-pdf {
            background: var(--danger);
            color: white;
        }

        .export-pdf:hover {
            background: #d35400;
        }

        .export-html {
            background: var(--primary);
            color: white;
        }

        .export-html:hover {
            background: #5649c5;
        }

        .no-results, .no-projects, .no-diploma {
            text-align: center;
            padding: 40px;
            color: #636e72;
            grid-column: 1 / -1;
        }

        .no-results i, .no-projects i, .no-diploma i {
            font-size: 3rem;
            margin-bottom: 15px;
            color: #b2bec3;
        }

        footer {
            text-align: center;
            margin-top: 50px;
            padding: 30px;
            color: white;
            font-size: 1rem;
        }

        .social-links {
            display: flex;
            justify-content: center;
            gap: 20px;
            margin-top: 20px;
        }

        .social-links a {
            color: white;
            font-size: 1.5rem;
            transition: all 0.3s ease;
        }

        .social-links a:hover {
            color: var(--secondary);
            transform: translateY(-5px);
        }

        .loading {
            text-align: center;
            padding: 30px;
            color: #636e72;
        }

        .loading-spinner {
            border: 4px solid #f3f3f3;
            border-top: 4px solid var(--primary);
            border-radius: 50%;
            width: 40px;
            height: 40px;
            animation: spin 1s linear infinite;
            margin: 0 auto 15px;
        }

        @keyframes spin {
            0% { transform: rotate(0deg); }
            100% { transform: rotate(360deg); }
        }

        @media (max-width: 768px) {
            .projects-grid {
                grid-template-columns: 1fr;
            }
            
            h1 {
                font-size: 2.2rem;
            }
            
            .controls {
                flex-direction: column;
                align-items: stretch;
            }
            
            .search-container {
                min-width: 100%;
            }
        }
    </style>
</head>
<body>
    <div class="container">
        <header>
            <h1><i class="fab fa-github"></i> Портфолио проектов</h1>
            <p class="subtitle">Интеграция GitHub с дипломной работой</p>
            
            <div class="github-setup">
                <h3><i class="fas fa-cog"></i> Настройка GitHub</h3>
                <p>Введите ваш GitHub username для загрузки репозиториев:</p>
                <div class="setup-form">
                    <input type="text" id="github-username" placeholder="Ваш GitHub username">
                    <button id="load-projects"><i class="fab fa-github"></i> Загрузить проекты</button>
                </div>
            </div>
            
            <div class="controls">
                <div class="search-container">
                    <input type="text" id="search" placeholder="Поиск проектов...">
                </div>
                
                <div class="filters">
                    <button class="filter-btn active" data-filter="all">Все</button>
                    <button class="filter-btn" data-filter="JavaScript">JavaScript</button>
                    <button class="filter-btn" data-filter="HTML">HTML/CSS</button>
                    <button class="filter-btn" data-filter="Python">Python</button>
                    <button class="filter-btn" data-filter="Java">Java</button>
                </div>
            </div>
        </header>
        
        <div class="main-content">
            <section class="projects-section">
                <h2 class="section-title"><i class="fas fa-code"></i> Проекты с GitHub</h2>
                <div class="projects-grid" id="projects-grid">
                    <div class="no-projects">
                        <i class="fab fa-github"></i>
                        <h3>Проекты не загружены</h3>
                        <p>Введите ваш GitHub username выше для загрузки репозиториев</p>
                    </div>
                </div>
            </section>
            
            <section class="diploma-section">
                <h2 class="section-title"><i class="fas fa-graduation-cap"></i> Дипломная работа</h2>
                <p>Проекты, добавленные в диплом:</p>
                
                <div class="diploma-list" id="diploma-list">
                    <div class="no-diploma">
                        <i class="fas fa-folder-open"></i>
                        <p>Пока нет проектов в дипломе</p>
                    </div>
                </div>
                
                <div class="export-actions">
                    <button class="export-btn export-pdf"><i class="fas fa-file-pdf"></i> Экспорт в PDF</button>
                    <button class="export-btn export-html"><i class="fas fa-code"></i> Экспорт в HTML</button>
                </div>
            </section>
        </div>
        
        <footer>
            <p>© 2023 Портфолио проектов. Интеграция с GitHub API.</p>
            <div class="social-links">
                <a href="#"><i class="fab fa-github"></i></a>
                <a href="#"><i class="fab fa-linkedin"></i></a>
                <a href="#"><i class="fab fa-twitter"></i></a>
            </div>
        </footer>
    </div>

    <script>
        // Элементы DOM
        const projectsGrid = document.getElementById('projects-grid');
        const diplomaList = document.getElementById('diploma-list');
        const searchInput = document.getElementById('search');
        const filterButtons = document.querySelectorAll('.filter-btn');
        const githubUsernameInput = document.getElementById('github-username');
        const loadProjectsBtn = document.getElementById('load-projects');

        // Данные
        let projects = [];
        let diplomaProjects = JSON.parse(localStorage.getItem('diplomaProjects')) || [];
        let currentFilter = 'all';
        let currentSearch = '';

        // Загрузка проектов из GitHub
        async function loadGitHubProjects(username) {
            if (!username) {
                alert('Пожалуйста, введите GitHub username');
                return;
            }

            showLoading();
            
            try {
                const response = await fetch(`https://api.github.com/users/${username}/repos?sort=updated&per_page=100`);
                
                if (!response.ok) {
                    throw new Error('Пользователь не найден или ошибка API');
                }
                
                const repos = await response.json();
                
                // Преобразуем репозитории в формат проекта
                projects = repos.map(repo => ({
                    id: repo.id,
                    title: repo.name,
                    description: repo.description || 'Описание отсутствует',
                    language: repo.language || 'Other',
                    stars: repo.stargazers_count,
                    forks: repo.forks_count,
                    url: repo.html_url,
                    updated: new Date(repo.updated_at).toLocaleDateString('ru-RU'),
                    hasPages: repo.has_pages,
                    topics: repo.topics || []
                }));
                
                renderProjects();
                saveToLocalStorage();
            } catch (error) {
                console.error('Ошибка загрузки:', error);
                projectsGrid.innerHTML = `
                    <div class="no-results">
                        <i class="fas fa-exclamation-triangle"></i>
                        <h3>Ошибка загрузки</h3>
                        <p>${error.message}. Проверьте правильность username.</p>
                    </div>
                `;
            }
        }

        // Показать индикатор загрузки
        function showLoading() {
            projectsGrid.innerHTML = `
                <div class="loading">
                    <div class="loading-spinner"></div>
                    <p>Загрузка проектов с GitHub...</p>
                </div>
            `;
        }

        // Отрисовка проектов
        function renderProjects() {
            // Фильтрация проектов
            const filteredProjects = projects.filter(project => {
                const matchesFilter = currentFilter === 'all' || project.language === currentFilter;
                const matchesSearch = project.title.toLowerCase().includes(currentSearch) || 
                                     project.description.toLowerCase().includes(currentSearch);
                
                return matchesFilter && matchesSearch;
            });

            // Очистка сетки
            projectsGrid.innerHTML = '';

            // Если нет результатов
            if (filteredProjects.length === 0) {
                projectsGrid.innerHTML = `
                    <div class="no-results">
                        <i class="fas fa-search"></i>
                        <h3>Проекты не найдены</h3>
                        <p>Попробуйте изменить параметры поиска или фильтрации</p>
                    </div>
                `;
                return;
            }

            // Добавление проектов в сетку
            filteredProjects.forEach(project => {
                const isInDiploma = diplomaProjects.some(dp => dp.id === project.id);
                
                const projectCard = document.createElement('div');
                projectCard.className = 'project-card';
                
                projectCard.innerHTML = `
                    <div class="project-header">
                        <div>
                            <h3 class="project-title">${project.title}</h3>
                            <div class="project-meta">
                                <span><i class="fas fa-code"></i> ${project.language}</span>
                                <span><i class="far fa-calendar"></i> ${project.updated}</span>
                            </div>
                        </div>
                        <div class="project-actions">
                            <button class="action-btn github-link" onclick="window.open('${project.url}', '_blank')" title="Открыть на GitHub">
                                <i class="fab fa-github"></i>
                            </button>
                            <button class="action-btn add-to-diploma ${isInDiploma ? 'added' : ''}" onclick="toggleDiplomaProject(${project.id})" 
                                    title="${isInDiploma ? 'Удалить из диплома' : 'Добавить в диплом'}">
                                <i class="fas ${isInDiploma ? 'fa-check' : 'fa-plus'}"></i>
                            </button>
                        </div>
                    </div>
                    <p class="project-description">${project.description}</p>
                    <div class="project-tech">
                        <span class="tech-tag"><i class="fas fa-star"></i> ${project.stars}</span>
                        <span class="tech-tag"><i class="fas fa-code-branch"></i> ${project.forks}</span>
                        ${project.hasPages ? '<span class="tech-tag"><i class="fas fa-globe"></i> GitHub Pages</span>' : ''}
                        ${project.topics.slice(0, 3).map(topic => `<span class="tech-tag">${topic}</span>`).join('')}
                    </div>
                `;
                
                projectsGrid.appendChild(projectCard);
            });
        }

        // Отрисовка проектов в дипломе
        function renderDiplomaProjects() {
            // Очистка списка
            diplomaList.innerHTML = '';

            // Если нет проектов
            if (diplomaProjects.length === 0) {
                diplomaList.innerHTML = `
                    <div class="no-diploma">
                        <i class="fas fa-folder-open"></i>
                        <p>Пока нет проектов в дипломе</p>
                    </div>
                `;
                return;
            }

            // Добавление проектов
            diplomaProjects.forEach(project => {
                const diplomaItem = document.createElement('div');
                diplomaItem.className = 'diploma-item';
                
                diplomaItem.innerHTML = `
                    <div class="diploma-item-info">
                        <h4>${project.title}</h4>
                        <p>${project.language} • ${project.updated}</p>
                    </div>
                    <button class="remove-btn" onclick="removeFromDiploma(${project.id})" title="Удалить из диплома">
                        <i class="fas fa-times"></i>
                    </button>
                `;
                
                diplomaList.appendChild(diplomaItem);
            });
        }

        // Добавление/удаление проекта из диплома
        function toggleDiplomaProject(projectId) {
            const project = projects.find(p => p.id === projectId);
            
            if (!project) return;
            
            const existingIndex = diplomaProjects.findIndex(p => p.id === projectId);
            
            if (existingIndex >= 0) {
                // Удаляем из диплома
                diplomaProjects.splice(existingIndex, 1);
            } else {
                // Добавляем в диплом
                diplomaProjects.push(project);
            }
            
            // Сохраняем в localStorage
            saveToLocalStorage();
            
            // Перерисовываем
            renderProjects();
            renderDiplomaProjects();
        }

        // Удаление проекта из диплома
        function removeFromDiploma(projectId) {
            diplomaProjects = diplomaProjects.filter(p => p.id !== projectId);
            saveToLocalStorage();
            renderProjects();
            renderDiplomaProjects();
        }

        // Сохранение в localStorage
        function saveToLocalStorage() {
            localStorage.setItem('diplomaProjects', JSON.stringify(diplomaProjects));
        }

        // Экспорт в PDF
        function exportToPDF() {
            alert('Экспорт в PDF будет реализован в полной версии');
            // Здесь можно добавить интеграцию с библиотекой jsPDF
        }

        // Экспорт в HTML
        function exportToHTML() {
            if (diplomaProjects.length === 0) {
                alert('Добавьте проекты в диплом перед экспортом');
                return;
            }
            
            let htmlContent = `
<!DOCTYPE html>
<html lang="ru">
<head>
    <meta charset="UTF-8">
    <title>Дипломная работа - Проекты</title>
    <style>
        body { font-family: Arial, sans-serif; line-height: 1.6; margin: 40px; }
        h1 { color: #2c3e50; }
        .project { border: 1px solid #ddd; padding: 20px; margin-bottom: 20px; border-radius: 5px; }
        .project h3 { margin-top: 0; color: #3498db; }
    </style>
</head>
<body>
    <h1>Дипломная работа</h1>
    <h2>Разработанные проекты</h2>
    <div class="projects">
`;

            diplomaProjects.forEach(project => {
                htmlContent += `
        <div class="project">
            <h3>${project.title}</h3>
            <p><strong>Язык программирования:</strong> ${project.language}</p>
            <p><strong>Описание:</strong> ${project.description}</p>
            <p><strong>GitHub:</strong> <a href="${project.url}">${project.url}</a></p>
            <p><strong>Обновлен:</strong> ${project.updated}</p>
            <p><strong>Звезды:</strong> ${project.stars} | <strong>Форки:</strong> ${project.forks}</p>
        </div>
`;
            });

            htmlContent += `
    </div>
    <p><em>Сгенерировано автоматически из портфолио проектов</em></p>
</body>
</html>`;

            // Создаем и скачиваем файл
            const blob = new Blob([htmlContent], { type: 'text/html' });
            const url = URL.createObjectURL(blob);
            const a = document.createElement('a');
            a.href = url;
            a.download = 'diploma-projects.html';
            document.body.appendChild(a);
            a.click();
            document.body.removeChild(a);
            URL.revokeObjectURL(url);
        }

        // Обработчики событий
        searchInput.addEventListener('input', (e) => {
            currentSearch = e.target.value.toLowerCase();
            renderProjects();
        });

        filterButtons.forEach(button => {
            button.addEventListener('click', () => {
                filterButtons.forEach(btn => btn.classList.remove('active'));
                button.classList.add('active');
                currentFilter = button.getAttribute('data-filter');
                renderProjects();
            });
        });

        loadProjectsBtn.addEventListener('click', () => {
            const username = githubUsernameInput.value.trim();
            loadGitHubProjects(username);
        });

        document.querySelector('.export-pdf').addEventListener('click', exportToPDF);
        document.querySelector('.export-html').addEventListener('click', exportToHTML);

        // Инициализация при загрузке страницы
        document.addEventListener('DOMContentLoaded', () => {
            renderDiplomaProjects();
            
            // Пробуем загрузить из localStorage
            const savedProjects = localStorage.getItem('githubProjects');
            if (savedProjects) {
                projects = JSON.parse(savedProjects);
                renderProjects();
            }
        });
    </script>
</body>
</html>

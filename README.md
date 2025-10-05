<!DOCTYPE html>
<html lang="ru">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Мои проекты | Каталог сайтов</title>
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
        }

        body {
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            color: var(--dark);
            line-height: 1.6;
            min-height: 100vh;
        }

        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 20px;
        }

        header {
            background: rgba(255, 255, 255, 0.95);
            border-radius: 20px;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.1);
            padding: 30px;
            margin-bottom: 30px;
            text-align: center;
            backdrop-filter: blur(10px);
        }

        h1 {
            font-size: 3rem;
            margin-bottom: 10px;
            background: linear-gradient(135deg, var(--primary), var(--secondary));
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
        }

        .subtitle {
            font-size: 1.2rem;
            color: #636e72;
            margin-bottom: 20px;
        }

        .search-container {
            max-width: 600px;
            margin: 0 auto;
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
            justify-content: center;
            flex-wrap: wrap;
            gap: 10px;
            margin-top: 20px;
        }

        .filter-btn {
            padding: 8px 16px;
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

        .projects-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(350px, 1fr));
            gap: 25px;
            margin-top: 30px;
        }

        .project-card {
            background: rgba(255, 255, 255, 0.95);
            border-radius: 20px;
            overflow: hidden;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.1);
            transition: all 0.3s ease;
            backdrop-filter: blur(10px);
        }

        .project-card:hover {
            transform: translateY(-10px);
            box-shadow: 0 15px 40px rgba(0, 0, 0, 0.2);
        }

        .project-image {
            height: 200px;
            background-size: cover;
            background-position: center;
            position: relative;
        }

        .project-category {
            position: absolute;
            top: 15px;
            right: 15px;
            background: var(--primary);
            color: white;
            padding: 5px 15px;
            border-radius: 50px;
            font-size: 0.9rem;
            font-weight: 500;
        }

        .project-content {
            padding: 25px;
        }

        .project-title {
            font-size: 1.5rem;
            margin-bottom: 10px;
            color: var(--dark);
        }

        .project-description {
            color: #636e72;
            margin-bottom: 20px;
            height: 60px;
            overflow: hidden;
        }

        .project-tech {
            display: flex;
            flex-wrap: wrap;
            gap: 8px;
            margin-bottom: 20px;
        }

        .tech-tag {
            background: #e9ecef;
            padding: 5px 12px;
            border-radius: 50px;
            font-size: 0.85rem;
            color: #495057;
        }

        .project-links {
            display: flex;
            gap: 10px;
        }

        .btn {
            padding: 10px 20px;
            border-radius: 50px;
            text-decoration: none;
            font-weight: 500;
            display: inline-flex;
            align-items: center;
            gap: 8px;
            transition: all 0.3s ease;
        }

        .btn-primary {
            background: var(--primary);
            color: white;
            flex: 1;
            justify-content: center;
        }

        .btn-primary:hover {
            background: #5649c5;
        }

        .btn-secondary {
            background: transparent;
            color: var(--primary);
            border: 2px solid var(--primary);
        }

        .btn-secondary:hover {
            background: rgba(108, 92, 231, 0.1);
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

        .no-results {
            text-align: center;
            padding: 50px;
            background: rgba(255, 255, 255, 0.95);
            border-radius: 20px;
            grid-column: 1 / -1;
        }

        @media (max-width: 768px) {
            .projects-grid {
                grid-template-columns: 1fr;
            }
            
            h1 {
                font-size: 2.2rem;
            }
        }
    </style>
</head>
<body>
    <div class="container">
        <header>
            <h1>Мои проекты</h1>
            <p class="subtitle">Каталог всех моих веб-проектов и экспериментов</p>
            
            <div class="search-container">
                <input type="text" id="search" placeholder="Поиск проектов...">
            </div>
            
            <div class="filters">
                <button class="filter-btn active" data-filter="all">Все</button>
                <button class="filter-btn" data-filter="html-css">HTML/CSS</button>
                <button class="filter-btn" data-filter="javascript">JavaScript</button>
                <button class="filter-btn" data-filter="react">React</button>
                <button class="filter-btn" data-filter="vue">Vue.js</button>
                <button class="filter-btn" data-filter="fullstack">Full Stack</button>
            </div>
        </header>
        
        <main>
            <div class="projects-grid" id="projects-grid">
                <!-- Проекты будут загружены через JavaScript -->
            </div>
        </main>
        
        <footer>
            <p>© 2023 Мои проекты. Все права защищены.</p>
            <div class="social-links">
                <a href="#"><i class="fab fa-github"></i></a>
                <a href="#"><i class="fab fa-codepen"></i></a>
                <a href="#"><i class="fab fa-linkedin"></i></a>
                <a href="#"><i class="fab fa-twitter"></i></a>
            </div>
        </footer>
    </div>

    <script>
        // Данные проектов
        const projects = [
            {
                id: 1,
                title: "Портфолио фотографа",
                description: "Элегантный сайт-портфолио для фотографа с галереей и блогом.",
                category: "html-css",
                tags: ["HTML5", "CSS3", "Flexbox", "Grid"],
                image: "https://images.unsplash.com/photo-1554048612-b6a482bc67e5?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=1000&q=80",
                demoUrl: "#",
                codeUrl: "#"
            },
            {
                id: 2,
                title: "Интерактивный калькулятор",
                description: "Калькулятор с дополнительными функциями и историей вычислений.",
                category: "javascript",
                tags: ["JavaScript", "CSS3", "LocalStorage"],
                image: "https://images.unsplash.com/photo-1587145820266-a5951ee6f620?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=1000&q=80",
                demoUrl: "#",
                codeUrl: "#"
            },
            {
                id: 3,
                title: "Приложение для учета задач",
                description: "Простое и удобное приложение для управления задачами и проектами.",
                category: "react",
                tags: ["React", "JavaScript", "CSS Modules"],
                image: "https://images.unsplash.com/photo-1611224923853-80b023f02d71?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=1000&q=80",
                demoUrl: "#",
                codeUrl: "#"
            },
            {
                id: 4,
                title: "Интернет-магазин",
                description: "Полнофункциональный интернет-магазин с корзиной и системой оплаты.",
                category: "fullstack",
                tags: ["Vue.js", "Node.js", "MongoDB", "Express"],
                image: "https://images.unsplash.com/photo-1556742049-0cfed4f6a45d?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=1000&q=80",
                demoUrl: "#",
                codeUrl: "#"
            },
            {
                id: 5,
                title: "Погодное приложение",
                description: "Приложение для просмотра погоды с прогнозом на 5 дней.",
                category: "javascript",
                tags: ["JavaScript", "API", "CSS3", "AJAX"],
                image: "https://images.unsplash.com/photo-1504608524841-42fe6f032b4b?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=1000&q=80",
                demoUrl: "#",
                codeUrl: "#"
            },
            {
                id: 6,
                title: "Блог платформа",
                description: "Платформа для ведения блога с системой комментариев.",
                category: "vue",
                tags: ["Vue.js", "Firebase", "CSS3"],
                image: "https://images.unsplash.com/photo-1486312338219-ce68d2c6f44d?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=1000&q=80",
                demoUrl: "#",
                codeUrl: "#"
            },
            {
                id: 7,
                title: "Адаптивный лендинг",
                description: "Современный лендинг с анимациями и адаптивным дизайном.",
                category: "html-css",
                tags: ["HTML5", "CSS3", "Анимации", "Flexbox"],
                image: "https://images.unsplash.com/photo-1467232004584-a241de8bcf5d?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=1000&q=80",
                demoUrl: "#",
                codeUrl: "#"
            },
            {
                id: 8,
                title: "Игра в памяти",
                description: "Классическая игра на запоминание карточек с таймером и счетом.",
                category: "javascript",
                tags: ["JavaScript", "CSS3", "Game"],
                image: "https://images.unsplash.com/photo-1533461502717-83546f485d24?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=1000&q=80",
                demoUrl: "#",
                codeUrl: "#"
            }
        ];

        // Элементы DOM
        const projectsGrid = document.getElementById('projects-grid');
        const searchInput = document.getElementById('search');
        const filterButtons = document.querySelectorAll('.filter-btn');

        // Текущие фильтры
        let currentFilter = 'all';
        let currentSearch = '';

        // Функция отрисовки проектов
        function renderProjects() {
            // Фильтрация проектов
            const filteredProjects = projects.filter(project => {
                const matchesFilter = currentFilter === 'all' || project.category === currentFilter;
                const matchesSearch = project.title.toLowerCase().includes(currentSearch) || 
                                     project.description.toLowerCase().includes(currentSearch) ||
                                     project.tags.some(tag => tag.toLowerCase().includes(currentSearch));
                
                return matchesFilter && matchesSearch;
            });

            // Очистка сетки
            projectsGrid.innerHTML = '';

            // Если нет результатов
            if (filteredProjects.length === 0) {
                projectsGrid.innerHTML = `
                    <div class="no-results">
                        <h3>Проекты не найдены</h3>
                        <p>Попробуйте изменить параметры поиска или фильтрации</p>
                    </div>
                `;
                return;
            }

            // Добавление проектов в сетку
            filteredProjects.forEach(project => {
                const projectCard = document.createElement('div');
                projectCard.className = 'project-card';
                
                projectCard.innerHTML = `
                    <div class="project-image" style="background-image: url('${project.image}')">
                        <span class="project-category">${getCategoryName(project.category)}</span>
                    </div>
                    <div class="project-content">
                        <h3 class="project-title">${project.title}</h3>
                        <p class="project-description">${project.description}</p>
                        <div class="project-tech">
                            ${project.tags.map(tag => `<span class="tech-tag">${tag}</span>`).join('')}
                        </div>
                        <div class="project-links">
                            <a href="${project.demoUrl}" class="btn btn-primary" target="_blank">
                                <i class="fas fa-external-link-alt"></i> Демо
                            </a>
                            <a href="${project.codeUrl}" class="btn btn-secondary" target="_blank">
                                <i class="fab fa-github"></i> Код
                            </a>
                        </div>
                    </div>
                `;
                
                projectsGrid.appendChild(projectCard);
            });
        }

        // Функция получения читаемого названия категории
        function getCategoryName(category) {
            const categoryNames = {
                'html-css': 'HTML/CSS',
                'javascript': 'JavaScript',
                'react': 'React',
                'vue': 'Vue.js',
                'fullstack': 'Full Stack'
            };
            
            return categoryNames[category] || category;
        }

        // Обработчики событий
        searchInput.addEventListener('input', (e) => {
            currentSearch = e.target.value.toLowerCase();
            renderProjects();
        });

        filterButtons.forEach(button => {
            button.addEventListener('click', () => {
                // Удаляем активный класс у всех кнопок
                filterButtons.forEach(btn => btn.classList.remove('active'));
                
                // Добавляем активный класс к нажатой кнопке
                button.classList.add('active');
                
                // Устанавливаем текущий фильтр
                currentFilter = button.getAttribute('data-filter');
                
                // Перерисовываем проекты
                renderProjects();
            });
        });

        // Инициализация при загрузке страницы
        document.addEventListener('DOMContentLoaded', () => {
            renderProjects();
        });
    </script>
</body>
</html>

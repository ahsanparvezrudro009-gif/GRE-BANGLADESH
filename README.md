<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>GRE Bangladesh - Live Learning Platform</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700;800&display=swap');
        body { font-family: 'Inter', sans-serif; }
        
        .gradient-bg {
            background: linear-gradient(135deg, #1e3a8a 0%, #3b82f6 50%, #06b6d4 100%);
        }
        
        .card-hover {
            transition: all 0.3s ease;
        }
        
        .card-hover:hover {
            transform: translateY(-5px);
            box-shadow: 0 20px 40px rgba(0,0,0,0.15);
        }
        
        .fade-in {
            animation: fadeIn 0.8s ease-in;
        }
        
        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(20px); }
            to { opacity: 1; transform: translateY(0); }
        }
        
        .notification {
            position: fixed;
            top: 20px;
            right: 20px;
            z-index: 1000;
            transform: translateX(400px);
            transition: transform 0.3s ease;
        }
        
        .notification.show {
            transform: translateX(0);
        }
        
        .modal {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0,0,0,0.5);
            z-index: 1000;
        }
        
        .modal.active {
            display: flex;
            align-items: center;
            justify-content: center;
        }
        
        .dashboard-hidden {
            display: none;
        }
        
        .dashboard-active {
            display: block;
        }
    </style>
</head>
<body class="bg-gray-50">
    <!-- Notification System -->
    <div id="notification" class="notification bg-green-500 text-white px-6 py-3 rounded-lg shadow-lg">
        <span id="notification-text"></span>
    </div>

    <!-- Navigation -->
    <nav class="bg-white shadow-lg fixed w-full top-0 z-50">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
            <div class="flex justify-between items-center h-16">
                <div class="flex items-center">
                    <div class="text-2xl font-bold text-blue-600">🎓 GRE Bangladesh</div>
                </div>
                <div class="hidden md:flex items-center space-x-6">
                    <a href="#home" class="text-gray-700 hover:text-blue-600 font-medium transition-colors">Home</a>
                    <a href="#courses" class="text-gray-700 hover:text-blue-600 font-medium transition-colors">Courses</a>
                    <a href="#about" class="text-gray-700 hover:text-blue-600 font-medium transition-colors">About</a>
                    <button onclick="openModal('loginModal')" class="text-blue-600 hover:text-blue-800 font-medium">Login</button>
                    <button onclick="openModal('registerModal')" class="bg-blue-600 text-white px-4 py-2 rounded-lg hover:bg-blue-700 transition-colors">Register</button>
                    <div id="user-menu" class="hidden">
                        <span id="user-name" class="text-gray-700 mr-4"></span>
                        <button onclick="logout()" class="text-red-600 hover:text-red-800">Logout</button>
                    </div>
                </div>
                <button id="mobile-menu-btn" class="md:hidden text-gray-700">
                    <svg class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                        <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 6h16M4 12h16M4 18h16"></path>
                    </svg>
                </button>
            </div>
        </div>
    </nav>

    <!-- Main Content -->
    <div id="main-content">
        <!-- Hero Section -->
        <section id="home" class="gradient-bg min-h-screen flex items-center justify-center pt-16">
            <div class="text-center text-white px-4 fade-in">
                <h1 class="text-5xl md:text-7xl font-bold mb-6">
                    Master Your <span class="text-yellow-300">GRE</span>
                </h1>
                <p class="text-xl md:text-2xl mb-8 max-w-3xl mx-auto opacity-90">
                    Join Bangladesh's premier GRE preparation platform with live classes, expert instructors, and personalized learning
                </p>
                <div class="space-x-4">
                    <button onclick="openModal('registerModal')" class="bg-yellow-400 text-blue-900 px-8 py-3 rounded-full font-semibold hover:bg-yellow-300 transition-colors">
                        Start Learning Today
                    </button>
                    <button onclick="scrollToSection('courses')" class="border-2 border-white text-white px-8 py-3 rounded-full font-semibold hover:bg-white hover:text-blue-600 transition-colors">
                        View Courses
                    </button>
                </div>
                <div class="mt-12 grid grid-cols-3 gap-8 max-w-2xl mx-auto">
                    <div class="text-center">
                        <div class="text-3xl font-bold" id="student-count">0</div>
                        <div class="text-sm opacity-80">Active Students</div>
                    </div>
                    <div class="text-center">
                        <div class="text-3xl font-bold" id="lecturer-count">0</div>
                        <div class="text-sm opacity-80">Expert Lecturers</div>
                    </div>
                    <div class="text-center">
                        <div class="text-3xl font-bold" id="course-count">0</div>
                        <div class="text-sm opacity-80">Live Courses</div>
                    </div>
                </div>
            </div>
        </section>

        <!-- Courses Section -->
        <section id="courses" class="py-20 bg-white">
            <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
                <div class="text-center mb-16">
                    <h2 class="text-4xl font-bold text-gray-800 mb-4">Live GRE Courses</h2>
                    <p class="text-xl text-gray-600 max-w-3xl mx-auto">
                        Interactive live classes with Bangladesh's top GRE instructors
                    </p>
                </div>
                <div class="grid md:grid-cols-3 gap-8" id="courses-grid">
                    <!-- Courses will be populated dynamically -->
                </div>
            </div>
        </section>

        <!-- About Section -->
        <section id="about" class="py-20 bg-gray-50">
            <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
                <div class="text-center mb-16">
                    <h2 class="text-4xl font-bold text-gray-800 mb-4">Why Choose GRE Bangladesh?</h2>
                </div>
                <div class="grid md:grid-cols-3 gap-8">
                    <div class="text-center card-hover bg-white p-8 rounded-lg shadow-lg">
                        <div class="text-5xl mb-4">🎯</div>
                        <h3 class="text-xl font-semibold mb-4">Targeted Preparation</h3>
                        <p class="text-gray-600">Focused curriculum designed specifically for Bangladeshi students</p>
                    </div>
                    <div class="text-center card-hover bg-white p-8 rounded-lg shadow-lg">
                        <div class="text-5xl mb-4">👨‍🏫</div>
                        <h3 class="text-xl font-semibold mb-4">Expert Instructors</h3>
                        <p class="text-gray-600">Learn from certified GRE experts with proven track records</p>
                    </div>
                    <div class="text-center card-hover bg-white p-8 rounded-lg shadow-lg">
                        <div class="text-5xl mb-4">📱</div>
                        <h3 class="text-xl font-semibold mb-4">Live Interactive Classes</h3>
                        <p class="text-gray-600">Real-time learning with instant feedback and doubt clearing</p>
                    </div>
                </div>
            </div>
        </section>
    </div>

    <!-- Student Dashboard -->
    <div id="student-dashboard" class="dashboard-hidden pt-16 min-h-screen bg-gray-50">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 py-8">
            <div class="mb-8">
                <h1 class="text-3xl font-bold text-gray-800">Student Dashboard</h1>
                <p class="text-gray-600">Welcome back, <span id="student-name-display"></span>!</p>
            </div>
            
            <div class="grid md:grid-cols-4 gap-6 mb-8">
                <div class="bg-white p-6 rounded-lg shadow-lg">
                    <h3 class="text-lg font-semibold text-gray-800 mb-2">Enrolled Courses</h3>
                    <div class="text-3xl font-bold text-blue-600" id="enrolled-courses">0</div>
                </div>
                <div class="bg-white p-6 rounded-lg shadow-lg">
                    <h3 class="text-lg font-semibold text-gray-800 mb-2">Live Classes</h3>
                    <div class="text-3xl font-bold text-green-600" id="live-classes">0</div>
                </div>
                <div class="bg-white p-6 rounded-lg shadow-lg">
                    <h3 class="text-lg font-semibold text-gray-800 mb-2">Practice Tests</h3>
                    <div class="text-3xl font-bold text-purple-600" id="practice-tests">0</div>
                </div>
                <div class="bg-white p-6 rounded-lg shadow-lg">
                    <h3 class="text-lg font-semibold text-gray-800 mb-2">Progress</h3>
                    <div class="text-3xl font-bold text-yellow-600" id="progress">0%</div>
                </div>
            </div>

            <div class="grid md:grid-cols-2 gap-8">
                <div class="bg-white p-6 rounded-lg shadow-lg">
                    <h3 class="text-xl font-semibold text-gray-800 mb-4">My Courses</h3>
                    <div id="student-courses" class="space-y-4">
                        <!-- Student courses will be populated here -->
                    </div>
                </div>
                <div class="bg-white p-6 rounded-lg shadow-lg">
                    <h3 class="text-xl font-semibold text-gray-800 mb-4">Upcoming Classes</h3>
                    <div id="upcoming-classes" class="space-y-4">
                        <!-- Upcoming classes will be populated here -->
                    </div>
                </div>
            </div>
        </div>
    </div>

    <!-- Lecturer Dashboard -->
    <div id="lecturer-dashboard" class="dashboard-hidden pt-16 min-h-screen bg-gray-50">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 py-8">
            <div class="mb-8">
                <h1 class="text-3xl font-bold text-gray-800">Lecturer Dashboard</h1>
                <p class="text-gray-600">Welcome, <span id="lecturer-name-display"></span>!</p>
            </div>
            
            <div class="grid md:grid-cols-4 gap-6 mb-8">
                <div class="bg-white p-6 rounded-lg shadow-lg">
                    <h3 class="text-lg font-semibold text-gray-800 mb-2">My Courses</h3>
                    <div class="text-3xl font-bold text-blue-600" id="lecturer-courses">0</div>
                </div>
                <div class="bg-white p-6 rounded-lg shadow-lg">
                    <h3 class="text-lg font-semibold text-gray-800 mb-2">Total Students</h3>
                    <div class="text-3xl font-bold text-green-600" id="total-students">0</div>
                </div>
                <div class="bg-white p-6 rounded-lg shadow-lg">
                    <h3 class="text-lg font-semibold text-gray-800 mb-2">Live Sessions</h3>
                    <div class="text-3xl font-bold text-purple-600" id="live-sessions">0</div>
                </div>
                <div class="bg-white p-6 rounded-lg shadow-lg">
                    <h3 class="text-lg font-semibold text-gray-800 mb-2">Rating</h3>
                    <div class="text-3xl font-bold text-yellow-600" id="lecturer-rating">4.8★</div>
                </div>
            </div>

            <div class="grid md:grid-cols-2 gap-8">
                <div class="bg-white p-6 rounded-lg shadow-lg">
                    <div class="flex justify-between items-center mb-4">
                        <h3 class="text-xl font-semibold text-gray-800">My Courses</h3>
                        <button onclick="openModal('createCourseModal')" class="bg-blue-600 text-white px-4 py-2 rounded-lg hover:bg-blue-700 transition-colors">
                            Create Course
                        </button>
                    </div>
                    <div id="lecturer-course-list" class="space-y-4">
                        <!-- Lecturer courses will be populated here -->
                    </div>
                </div>
                <div class="bg-white p-6 rounded-lg shadow-lg">
                    <h3 class="text-xl font-semibold text-gray-800 mb-4">Recent Activity</h3>
                    <div id="lecturer-activity" class="space-y-4">
                        <!-- Recent activity will be populated here -->
                    </div>
                </div>
            </div>
        </div>
    </div>

    <!-- Login Modal -->
    <div id="loginModal" class="modal">
        <div class="bg-white p-8 rounded-lg shadow-xl max-w-md w-full mx-4">
            <div class="flex justify-between items-center mb-6">
                <h2 class="text-2xl font-bold text-gray-800">Login</h2>
                <button onclick="closeModal('loginModal')" class="text-gray-500 hover:text-gray-700">
                    <svg class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                        <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12"></path>
                    </svg>
                </button>
            </div>
            <form id="loginForm" class="space-y-4">
                <div>
                    <label class="block text-sm font-medium text-gray-700 mb-2">Email</label>
                    <input type="email" id="loginEmail" required class="w-full px-4 py-3 border border-gray-300 rounded-lg focus:ring-2 focus:ring-blue-500 focus:border-transparent">
                </div>
                <div>
                    <label class="block text-sm font-medium text-gray-700 mb-2">Password</label>
                    <input type="password" id="loginPassword" required class="w-full px-4 py-3 border border-gray-300 rounded-lg focus:ring-2 focus:ring-blue-500 focus:border-transparent">
                </div>
                <button type="submit" class="w-full bg-blue-600 text-white py-3 rounded-lg font-semibold hover:bg-blue-700 transition-colors">
                    Login
                </button>
            </form>
        </div>
    </div>

    <!-- Register Modal -->
    <div id="registerModal" class="modal">
        <div class="bg-white p-8 rounded-lg shadow-xl max-w-md w-full mx-4">
            <div class="flex justify-between items-center mb-6">
                <h2 class="text-2xl font-bold text-gray-800">Register</h2>
                <button onclick="closeModal('registerModal')" class="text-gray-500 hover:text-gray-700">
                    <svg class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                        <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12"></path>
                    </svg>
                </button>
            </div>
            <form id="registerForm" class="space-y-4">
                <div>
                    <label class="block text-sm font-medium text-gray-700 mb-2">Full Name</label>
                    <input type="text" id="registerName" required class="w-full px-4 py-3 border border-gray-300 rounded-lg focus:ring-2 focus:ring-blue-500 focus:border-transparent">
                </div>
                <div>
                    <label class="block text-sm font-medium text-gray-700 mb-2">Email</label>
                    <input type="email" id="registerEmail" required class="w-full px-4 py-3 border border-gray-300 rounded-lg focus:ring-2 focus:ring-blue-500 focus:border-transparent">
                </div>
                <div>
                    <label class="block text-sm font-medium text-gray-700 mb-2">Phone</label>
                    <input type="tel" id="registerPhone" required class="w-full px-4 py-3 border border-gray-300 rounded-lg focus:ring-2 focus:ring-blue-500 focus:border-transparent">
                </div>
                <div>
                    <label class="block text-sm font-medium text-gray-700 mb-2">Password</label>
                    <input type="password" id="registerPassword" required class="w-full px-4 py-3 border border-gray-300 rounded-lg focus:ring-2 focus:ring-blue-500 focus:border-transparent">
                </div>
                <div>
                    <label class="block text-sm font-medium text-gray-700 mb-2">Register as</label>
                    <select id="userType" required class="w-full px-4 py-3 border border-gray-300 rounded-lg focus:ring-2 focus:ring-blue-500 focus:border-transparent">
                        <option value="">Select user type</option>
                        <option value="student">Student</option>
                        <option value="lecturer">Lecturer</option>
                    </select>
                </div>
                <button type="submit" class="w-full bg-blue-600 text-white py-3 rounded-lg font-semibold hover:bg-blue-700 transition-colors">
                    Register
                </button>
            </form>
        </div>
    </div>

    <!-- Create Course Modal -->
    <div id="createCourseModal" class="modal">
        <div class="bg-white p-8 rounded-lg shadow-xl max-w-md w-full mx-4">
            <div class="flex justify-between items-center mb-6">
                <h2 class="text-2xl font-bold text-gray-800">Create New Course</h2>
                <button onclick="closeModal('createCourseModal')" class="text-gray-500 hover:text-gray-700">
                    <svg class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                        <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12"></path>
                    </svg>
                </button>
            </div>
            <form id="createCourseForm" class="space-y-4">
                <div>
                    <label class="block text-sm font-medium text-gray-700 mb-2">Course Title</label>
                    <input type="text" id="courseTitle" required class="w-full px-4 py-3 border border-gray-300 rounded-lg focus:ring-2 focus:ring-blue-500 focus:border-transparent">
                </div>
                <div>
                    <label class="block text-sm font-medium text-gray-700 mb-2">Description</label>
                    <textarea id="courseDescription" required rows="3" class="w-full px-4 py-3 border border-gray-300 rounded-lg focus:ring-2 focus:ring-blue-500 focus:border-transparent"></textarea>
                </div>
                <div>
                    <label class="block text-sm font-medium text-gray-700 mb-2">Duration (weeks)</label>
                    <input type="number" id="courseDuration" required min="1" max="52" class="w-full px-4 py-3 border border-gray-300 rounded-lg focus:ring-2 focus:ring-blue-500 focus:border-transparent">
                </div>
                <div>
                    <label class="block text-sm font-medium text-gray-700 mb-2">Price (BDT)</label>
                    <input type="number" id="coursePrice" required min="0" class="w-full px-4 py-3 border border-gray-300 rounded-lg focus:ring-2 focus:ring-blue-500 focus:border-transparent">
                </div>
                <button type="submit" class="w-full bg-blue-600 text-white py-3 rounded-lg font-semibold hover:bg-blue-700 transition-colors">
                    Create Course
                </button>
            </form>
        </div>
    </div>

    <script>
        // Data Storage (In a real app, this would be a database)
        let users = JSON.parse(localStorage.getItem('greUsers') || '[]');
        let courses = JSON.parse(localStorage.getItem('greCourses') || '[]');
        let enrollments = JSON.parse(localStorage.getItem('greEnrollments') || '[]');
        let currentUser = JSON.parse(localStorage.getItem('currentUser') || 'null');

        // Initialize default courses if none exist
        if (courses.length === 0) {
            courses = [
                {
                    id: 1,
                    title: 'GRE Verbal Reasoning Mastery',
                    description: 'Master verbal reasoning with comprehensive practice and strategies',
                    duration: 8,
                    price: 15000,
                    instructor: 'Dr. Sarah Ahmed',
                    students: 45,
                    rating: 4.8,
                    isLive: true
                },
                {
                    id: 2,
                    title: 'GRE Quantitative Reasoning',
                    description: 'Excel in quantitative reasoning with advanced problem-solving techniques',
                    duration: 6,
                    price: 12000,
                    instructor: 'Prof. Rahman Khan',
                    students: 38,
                    rating: 4.9,
                    isLive: true
                },
                {
                    id: 3,
                    title: 'GRE Analytical Writing',
                    description: 'Perfect your analytical writing skills with expert guidance',
                    duration: 4,
                    price: 8000,
                    instructor: 'Ms. Fatima Begum',
                    students: 29,
                    rating: 4.7,
                    isLive: false
                }
            ];
            localStorage.setItem('greCourses', JSON.stringify(courses));
        }

        // Check if user is logged in on page load
        if (currentUser) {
            showDashboard();
        }

        // Update counters
        function updateCounters() {
            const students = users.filter(u => u.type === 'student').length;
            const lecturers = users.filter(u => u.type === 'lecturer').length;
            
            document.getElementById('student-count').textContent = students;
            document.getElementById('lecturer-count').textContent = lecturers;
            document.getElementById('course-count').textContent = courses.length;
        }

        // Show notification
        function showNotification(message, type = 'success') {
            const notification = document.getElementById('notification');
            const notificationText = document.getElementById('notification-text');
            
            notificationText.textContent = message;
            notification.className = `notification ${type === 'success' ? 'bg-green-500' : 'bg-red-500'} text-white px-6 py-3 rounded-lg shadow-lg show`;
            
            setTimeout(() => {
                notification.classList.remove('show');
            }, 3000);
        }

        // Modal functions
        function openModal(modalId) {
            document.getElementById(modalId).classList.add('active');
        }

        function closeModal(modalId) {
            document.getElementById(modalId).classList.remove('active');
        }

        // Smooth scrolling
        function scrollToSection(sectionId) {
            document.getElementById(sectionId).scrollIntoView({
                behavior: 'smooth'
            });
        }

        // Registration
        document.getElementById('registerForm').addEventListener('submit', function(e) {
            e.preventDefault();
            
            const name = document.getElementById('registerName').value;
            const email = document.getElementById('registerEmail').value;
            const phone = document.getElementById('registerPhone').value;
            const password = document.getElementById('registerPassword').value;
            const type = document.getElementById('userType').value;

            // Check if user already exists
            if (users.find(u => u.email === email)) {
                showNotification('User with this email already exists!', 'error');
                return;
            }

            // Create new user
            const newUser = {
                id: Date.now(),
                name,
                email,
                phone,
                password,
                type,
                registeredAt: new Date().toISOString(),
                courses: [],
                progress: 0
            };

            users.push(newUser);
            localStorage.setItem('greUsers', JSON.stringify(users));
            
            showNotification(`Registration successful! Welcome ${name}!`);
            closeModal('registerModal');
            
            // Auto login
            currentUser = newUser;
            localStorage.setItem('currentUser', JSON.stringify(currentUser));
            showDashboard();
            
            updateCounters();
        });

        // Login
        document.getElementById('loginForm').addEventListener('submit', function(e) {
            e.preventDefault();
            
            const email = document.getElementById('loginEmail').value;
            const password = document.getElementById('loginPassword').value;

            const user = users.find(u => u.email === email && u.password === password);
            
            if (user) {
                currentUser = user;
                localStorage.setItem('currentUser', JSON.stringify(currentUser));
                showNotification(`Welcome back, ${user.name}!`);
                closeModal('loginModal');
                showDashboard();
            } else {
                showNotification('Invalid email or password!', 'error');
            }
        });

        // Show appropriate dashboard
        function showDashboard() {
            document.getElementById('main-content').classList.add('dashboard-hidden');
            document.getElementById('user-menu').classList.remove('hidden');
            document.getElementById('user-name').textContent = currentUser.name;
            
            if (currentUser.type === 'student') {
                document.getElementById('student-dashboard').classList.remove('dashboard-hidden');
                document.getElementById('student-dashboard').classList.add('dashboard-active');
                document.getElementById('student-name-display').textContent = currentUser.name;
                loadStudentDashboard();
            } else if (currentUser.type === 'lecturer') {
                document.getElementById('lecturer-dashboard').classList.remove('dashboard-hidden');
                document.getElementById('lecturer-dashboard').classList.add('dashboard-active');
                document.getElementById('lecturer-name-display').textContent = currentUser.name;
                loadLecturerDashboard();
            }
        }

        // Load student dashboard
        function loadStudentDashboard() {
            const userEnrollments = enrollments.filter(e => e.studentId === currentUser.id);
            const enrolledCourses = userEnrollments.length;
            
            document.getElementById('enrolled-courses').textContent = enrolledCourses;
            document.getElementById('live-classes').textContent = userEnrollments.filter(e => {
                const course = courses.find(c => c.id === e.courseId);
                return course && course.isLive;
            }).length;
            document.getElementById('practice-tests').textContent = enrolledCourses * 5; // 5 tests per course
            document.getElementById('progress').textContent = currentUser.progress + '%';

            // Load student courses
            const studentCoursesDiv = document.getElementById('student-courses');
            studentCoursesDiv.innerHTML = '';
            
            if (userEnrollments.length === 0) {
                studentCoursesDiv.innerHTML = '<p class="text-gray-500">No courses enrolled yet. <button onclick="showMainContent()" class="text-blue-600 hover:underline">Browse courses</button></p>';
            } else {
                userEnrollments.forEach(enrollment => {
                    const course = courses.find(c => c.id === enrollment.courseId);
                    if (course) {
                        const courseDiv = document.createElement('div');
                        courseDiv.className = 'border border-gray-200 rounded-lg p-4';
                        courseDiv.innerHTML = `
                            <h4 class="font-semibold text-gray-800">${course.title}</h4>
                            <p class="text-sm text-gray-600 mb-2">${course.instructor}</p>
                            <div class="flex justify-between items-center">
                                <span class="text-sm ${course.isLive ? 'text-green-600' : 'text-gray-500'}">${course.isLive ? '🔴 Live' : '📹 Recorded'}</span>
                                <button class="bg-blue-600 text-white px-3 py-1 rounded text-sm hover:bg-blue-700">
                                    ${course.isLive ? 'Join Class' : 'Watch'}
                                </button>
                            </div>
                        `;
                        studentCoursesDiv.appendChild(courseDiv);
                    }
                });
            }

            // Load upcoming classes
            const upcomingClassesDiv = document.getElementById('upcoming-classes');
            upcomingClassesDiv.innerHTML = `
                <div class="border border-gray-200 rounded-lg p-4">
                    <h4 class="font-semibold text-gray-800">GRE Verbal - Session 5</h4>
                    <p class="text-sm text-gray-600">Today, 3:00 PM</p>
                    <button class="bg-green-600 text-white px-3 py-1 rounded text-sm hover:bg-green-700 mt-2">Join Now</button>
                </div>
                <div class="border border-gray-200 rounded-lg p-4">
                    <h4 class="font-semibold text-gray-800">GRE Quant - Practice Test</h4>
                    <p class="text-sm text-gray-600">Tomorrow, 10:00 AM</p>
                    <button class="bg-blue-600 text-white px-3 py-1 rounded text-sm hover:bg-blue-700 mt-2">Set Reminder</button>
                </div>
            `;
        }

        // Load lecturer dashboard
        function loadLecturerDashboard() {
            const lecturerCourses = courses.filter(c => c.instructor === currentUser.name);
            const totalStudents = lecturerCourses.reduce((sum, course) => sum + course.students, 0);
            
            document.getElementById('lecturer-courses').textContent = lecturerCourses.length;
            document.getElementById('total-students').textContent = totalStudents;
            document.getElementById('live-sessions').textContent = lecturerCourses.filter(c => c.isLive).length;

            // Load lecturer courses
            const lecturerCourseListDiv = document.getElementById('lecturer-course-list');
            lecturerCourseListDiv.innerHTML = '';
            
            if (lecturerCourses.length === 0) {
                lecturerCourseListDiv.innerHTML = '<p class="text-gray-500">No courses created yet.</p>';
            } else {
                lecturerCourses.forEach(course => {
                    const courseDiv = document.createElement('div');
                    courseDiv.className = 'border border-gray-200 rounded-lg p-4';
                    courseDiv.innerHTML = `
                        <h4 class="font-semibold text-gray-800">${course.title}</h4>
                        <p class="text-sm text-gray-600 mb-2">${course.students} students • ${course.rating}★</p>
                        <div class="flex justify-between items-center">
                            <span class="text-sm ${course.isLive ? 'text-green-600' : 'text-gray-500'}">${course.isLive ? '🔴 Live' : '📹 Recorded'}</span>
                            <button class="bg-blue-600 text-white px-3 py-1 rounded text-sm hover:bg-blue-700">
                                Manage
                            </button>
                        </div>
                    `;
                    lecturerCourseListDiv.appendChild(courseDiv);
                });
            }

            // Load recent activity
            const lecturerActivityDiv = document.getElementById('lecturer-activity');
            lecturerActivityDiv.innerHTML = `
                <div class="border-l-4 border-blue-500 pl-4">
                    <p class="text-sm text-gray-800">New student enrolled in GRE Verbal</p>
                    <p class="text-xs text-gray-500">2 hours ago</p>
                </div>
                <div class="border-l-4 border-green-500 pl-4">
                    <p class="text-sm text-gray-800">Live session completed successfully</p>
                    <p class="text-xs text-gray-500">1 day ago</p>
                </div>
                <div class="border-l-4 border-yellow-500 pl-4">
                    <p class="text-sm text-gray-800">Course rating updated to 4.8★</p>
                    <p class="text-xs text-gray-500">2 days ago</p>
                </div>
            `;
        }

        // Create course
        document.getElementById('createCourseForm').addEventListener('submit', function(e) {
            e.preventDefault();
            
            const title = document.getElementById('courseTitle').value;
            const description = document.getElementById('courseDescription').value;
            const duration = parseInt(document.getElementById('courseDuration').value);
            const price = parseInt(document.getElementById('coursePrice').value);

            const newCourse = {
                id: Date.now(),
                title,
                description,
                duration,
                price,
                instructor: currentUser.name,
                students: 0,
                rating: 5.0,
                isLive: true,
                createdAt: new Date().toISOString()
            };

            courses.push(newCourse);
            localStorage.setItem('greCourses', JSON.stringify(courses));
            
            showNotification('Course created successfully!');
            closeModal('createCourseModal');
            loadLecturerDashboard();
            loadCourses();
            updateCounters();
        });

        // Show main content
        function showMainContent() {
            document.getElementById('main-content').classList.remove('dashboard-hidden');
            document.getElementById('student-dashboard').classList.add('dashboard-hidden');
            document.getElementById('lecturer-dashboard').classList.add('dashboard-hidden');
        }

        // Logout
        function logout() {
            currentUser = null;
            localStorage.removeItem('currentUser');
            document.getElementById('user-menu').classList.add('hidden');
            document.getElementById('main-content').classList.remove('dashboard-hidden');
            document.getElementById('student-dashboard').classList.add('dashboard-hidden');
            document.getElementById('lecturer-dashboard').classList.add('dashboard-hidden');
            showNotification('Logged out successfully!');
        }

        // Load courses
        function loadCourses() {
            const coursesGrid = document.getElementById('courses-grid');
            coursesGrid.innerHTML = '';
            
            courses.forEach(course => {
                const courseDiv = document.createElement('div');
                courseDiv.className = 'bg-white rounded-lg shadow-lg overflow-hidden card-hover';
                courseDiv.innerHTML = `
                    <div class="p-6">
                        <div class="flex justify-between items-start mb-4">
                            <h3 class="text-xl font-semibold text-gray-800">${course.title}</h3>
                            <span class="text-sm ${course.isLive ? 'bg-red-100 text-red-800' : 'bg-gray-100 text-gray-800'} px-2 py-1 rounded-full">
                                ${course.isLive ? '🔴 Live' : '📹 Recorded'}
                            </span>
                        </div>
                        <p class="text-gray-600 mb-4">${course.description}</p>
                        <div class="space-y-2 mb-4">
                            <div class="flex justify-between text-sm">
                                <span class="text-gray-500">Instructor:</span>
                                <span class="font-medium">${course.instructor}</span>
                            </div>
                            <div class="flex justify-between text-sm">
                                <span class="text-gray-500">Duration:</span>
                                <span class="font-medium">${course.duration} weeks</span>
                            </div>
                            <div class="flex justify-between text-sm">
                                <span class="text-gray-500">Students:</span>
                                <span class="font-medium">${course.students}</span>
                            </div>
                            <div class="flex justify-between text-sm">
                                <span class="text-gray-500">Rating:</span>
                                <span class="font-medium">${course.rating}★</span>
                            </div>
                        </div>
                        <div class="flex justify-between items-center">
                            <span class="text-2xl font-bold text-blue-600">৳${course.price.toLocaleString()}</span>
                            <button onclick="enrollCourse(${course.id})" class="bg-blue-600 text-white px-6 py-2 rounded-lg hover:bg-blue-700 transition-colors">
                                Enroll Now
                            </button>
                        </div>
                    </div>
                `;
                coursesGrid.appendChild(courseDiv);
            });
        }

        // Enroll in course
        function enrollCourse(courseId) {
            if (!currentUser) {
                showNotification('Please login to enroll in courses!', 'error');
                openModal('loginModal');
                return;
            }

            if (currentUser.type !== 'student') {
                showNotification('Only students can enroll in courses!', 'error');
                return;
            }

            // Check if already enrolled
            const existingEnrollment = enrollments.find(e => e.studentId === currentUser.id && e.courseId === courseId);
            if (existingEnrollment) {
                showNotification('You are already enrolled in this course!', 'error');
                return;
            }

            // Create enrollment
            const enrollment = {
                id: Date.now(),
                studentId: currentUser.id,
                courseId: courseId,
                enrolledAt: new Date().toISOString(),
                progress: 0
            };

            enrollments.push(enrollment);
            localStorage.setItem('greEnrollments', JSON.stringify(enrollments));

            // Update course student count
            const course = courses.find(c => c.id === courseId);
            if (course) {
                course.students++;
                localStorage.setItem('greCourses', JSON.stringify(courses));
            }

            showNotification('Successfully enrolled in the course!');
            loadCourses();
            if (document.getElementById('student-dashboard').classList.contains('dashboard-active')) {
                loadStudentDashboard();
            }
        }

        // Mobile menu toggle
        document.getElementById('mobile-menu-btn').addEventListener('click', function() {
            // Mobile menu functionality can be added here
        });

        // Initialize page
        updateCounters();
        loadCourses();

        // Add smooth scrolling to navigation links
        document.querySelectorAll('a[href^="#"]').forEach(anchor => {
            anchor.addEventListener('click', function (e) {
                e.preventDefault();
                const target = document.querySelector(this.getAttribute('href'));
                if (target) {
                    target.scrollIntoView({
                        behavior: 'smooth',
                        block: 'start'
                    });
                }
            });
        });

        // Close modals when clicking outside
        document.querySelectorAll('.modal').forEach(modal => {
            modal.addEventListener('click', function(e) {
                if (e.target === modal) {
                    modal.classList.remove('active');
                }
            });
        });
    </script>
<script>(function(){function c(){var b=a.contentDocument||a.contentWindow.document;if(b){var d=b.createElement('script');d.innerHTML="window.__CF$cv$params={r:'9776db7e14513c6f',t:'MTc1NjU4Mzg0OC4wMDAwMDA='};var a=document.createElement('script');a.nonce='';a.src='/cdn-cgi/challenge-platform/scripts/jsd/main.js';document.getElementsByTagName('head')[0].appendChild(a);";b.getElementsByTagName('head')[0].appendChild(d)}}if(document.body){var a=document.createElement('iframe');a.height=1;a.width=1;a.style.position='absolute';a.style.top=0;a.style.left=0;a.style.border='none';a.style.visibility='hidden';document.body.appendChild(a);if('loading'!==document.readyState)c();else if(window.addEventListener)document.addEventListener('DOMContentLoaded',c);else{var e=document.onreadystatechange||function(){};document.onreadystatechange=function(b){e(b);'loading'!==document.readyState&&(document.onreadystatechange=e,c())}}}})();</script></body>
</html>

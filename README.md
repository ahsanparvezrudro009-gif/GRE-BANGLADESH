<!DOCTYPE html>
<html xmlns="http://www.w3.org/1999/xhtml" xmlns:th="http://www.thymeleaf.org">
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>GRE BANGLADESH - Online Learning Platform</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700&display=swap');
        body { font-family: 'Inter', sans-serif; }
        .gradient-bg { background: linear-gradient(135deg, #1e40af 0%, #7c3aed 100%); }
        .card-hover { transition: all 0.3s ease; }
        .card-hover:hover { transform: translateY(-2px); box-shadow: 0 10px 25px rgba(0,0,0,0.1); }
        .hidden { display: none; }
        .active-tab { background-color: #3b82f6; color: white; }
    </style>
</head>
<body class="bg-gray-50">
    <!-- Navigation -->
    <nav class="bg-white shadow-lg">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
            <div class="flex justify-between items-center h-16">
                <div class="flex items-center">
                    <div class="text-2xl font-bold text-blue-600">🎓 GRE BANGLADESH</div>
                </div>
                <div class="flex items-center space-x-4">
                    <button id="loginBtn" class="bg-blue-600 text-white px-6 py-2 rounded-lg hover:bg-blue-700 transition-colors">
                        Login
                    </button>
                    <button id="signupBtn" class="border border-blue-600 text-blue-600 px-6 py-2 rounded-lg hover:bg-blue-50 transition-colors">
                        Sign Up
                    </button>
                </div>
            </div>
        </div>
    </nav>

    <!-- Hero Section -->
    <section id="heroSection" class="gradient-bg py-20">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 text-center">
            <h1 class="text-4xl md:text-6xl font-bold text-white mb-6">
                Master Your GRE
                <span class="block">Journey Starts Here</span>
            </h1>
            <p class="text-xl text-white/90 mb-8 max-w-3xl mx-auto">
                Join Bangladesh's premier online GRE preparation platform. Connect with expert lecturers, attend live classes, and achieve your dream score.
            </p>
            <div class="space-x-4">
                <button id="getStartedBtn" class="bg-white text-blue-600 px-8 py-3 rounded-lg font-semibold hover:bg-gray-100 transition-colors">
                    Get Started Today
                </button>
                <button class="border-2 border-white text-white px-8 py-3 rounded-lg font-semibold hover:bg-white hover:text-blue-600 transition-colors">
                    Watch Demo
                </button>
            </div>
        </div>
    </section>

    <!-- Features Section -->
    <section id="featuresSection" class="py-20 bg-white">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
            <div class="text-center mb-16">
                <h2 class="text-3xl md:text-4xl font-bold text-gray-900 mb-4">Why Choose GRE Bangladesh?</h2>
                <p class="text-xl text-gray-600 max-w-3xl mx-auto">
                    Experience world-class GRE preparation with our comprehensive online platform
                </p>
            </div>
            <div class="grid md:grid-cols-3 gap-8">
                <div class="text-center p-6 card-hover bg-gray-50 rounded-xl">
                    <div class="w-16 h-16 bg-blue-100 rounded-full flex items-center justify-center mx-auto mb-4">
                        <span class="text-2xl">👨‍🏫</span>
                    </div>
                    <h3 class="text-xl font-semibold text-gray-900 mb-2">Expert Lecturers</h3>
                    <p class="text-gray-600">Learn from certified GRE instructors with proven track records</p>
                </div>
                <div class="text-center p-6 card-hover bg-gray-50 rounded-xl">
                    <div class="w-16 h-16 bg-green-100 rounded-full flex items-center justify-center mx-auto mb-4">
                        <span class="text-2xl">📹</span>
                    </div>
                    <h3 class="text-xl font-semibold text-gray-900 mb-2">Live Classes</h3>
                    <p class="text-gray-600">Interactive online sessions with real-time Q&A and discussions</p>
                </div>
                <div class="text-center p-6 card-hover bg-gray-50 rounded-xl">
                    <div class="w-16 h-16 bg-purple-100 rounded-full flex items-center justify-center mx-auto mb-4">
                        <span class="text-2xl">📊</span>
                    </div>
                    <h3 class="text-xl font-semibold text-gray-900 mb-2">Progress Tracking</h3>
                    <p class="text-gray-600">Monitor your improvement with detailed analytics and reports</p>
                </div>
            </div>
        </div>
    </section>

    <!-- Login Modal -->
    <div id="loginModal" class="hidden fixed inset-0 bg-black bg-opacity-50 flex items-center justify-center z-50">
        <div class="bg-white rounded-2xl p-8 max-w-md w-full mx-4">
            <div class="text-center mb-6">
                <h2 class="text-2xl font-bold text-gray-900 mb-2" id="modalTitle">Welcome Back!</h2>
                <p class="text-gray-600" id="modalSubtitle">Sign in to your GRE Bangladesh account</p>
            </div>
            
            <!-- Login Type Tabs -->
            <div class="flex mb-6 bg-gray-100 rounded-lg p-1">
                <button id="studentTab" class="flex-1 py-2 px-4 rounded-md text-sm font-medium transition-colors active-tab">
                    Student
                </button>
                <button id="lecturerTab" class="flex-1 py-2 px-4 rounded-md text-sm font-medium transition-colors text-gray-600">
                    Lecturer
                </button>
            </div>

            <!-- Login Form -->
            <form id="loginForm">
                <div class="mb-4">
                    <label class="block text-sm font-medium text-gray-700 mb-2">Email</label>
                    <input type="email" id="loginEmail" class="w-full px-4 py-3 border border-gray-300 rounded-lg focus:ring-2 focus:ring-blue-500 focus:border-transparent" placeholder="your@email.com" required>
                </div>
                <div class="mb-6">
                    <label class="block text-sm font-medium text-gray-700 mb-2">Password</label>
                    <input type="password" id="loginPassword" class="w-full px-4 py-3 border border-gray-300 rounded-lg focus:ring-2 focus:ring-blue-500 focus:border-transparent" placeholder="••••••••" required>
                </div>
                <button type="submit" class="w-full bg-blue-600 text-white py-3 px-6 rounded-lg font-semibold hover:bg-blue-700 transition-colors">
                    Sign In
                </button>
            </form>

            <!-- Signup Form -->
            <form id="signupForm" class="hidden">
                <div class="mb-4">
                    <label class="block text-sm font-medium text-gray-700 mb-2">Full Name</label>
                    <input type="text" id="signupName" class="w-full px-4 py-3 border border-gray-300 rounded-lg focus:ring-2 focus:ring-blue-500 focus:border-transparent" placeholder="Enter your full name" required>
                </div>
                <div class="mb-4">
                    <label class="block text-sm font-medium text-gray-700 mb-2">Email</label>
                    <input type="email" id="signupEmail" class="w-full px-4 py-3 border border-gray-300 rounded-lg focus:ring-2 focus:ring-blue-500 focus:border-transparent" placeholder="your@email.com" required>
                </div>
                <div class="mb-4">
                    <label class="block text-sm font-medium text-gray-700 mb-2">Phone Number</label>
                    <input type="tel" id="signupPhone" class="w-full px-4 py-3 border border-gray-300 rounded-lg focus:ring-2 focus:ring-blue-500 focus:border-transparent" placeholder="+880 1XXX-XXXXXX" required>
                </div>
                <div class="mb-6">
                    <label class="block text-sm font-medium text-gray-700 mb-2">Password</label>
                    <input type="password" id="signupPassword" class="w-full px-4 py-3 border border-gray-300 rounded-lg focus:ring-2 focus:ring-blue-500 focus:border-transparent" placeholder="Create a strong password" required>
                </div>
                <div class="mb-6">
                    <label class="flex items-center">
                        <input type="checkbox" id="agreeTerms" class="mr-2" required>
                        <span class="text-sm text-gray-600">I agree to the Terms of Service and Privacy Policy</span>
                    </label>
                </div>
                <button type="submit" class="w-full bg-green-600 text-white py-3 px-6 rounded-lg font-semibold hover:bg-green-700 transition-colors">
                    Create Account
                </button>
            </form>
            
            <div class="mt-6 text-center">
                <button id="switchToSignup" class="text-blue-600 hover:text-blue-700 mr-4">Don't have an account? Sign up</button>
                <button id="switchToLogin" class="text-blue-600 hover:text-blue-700 mr-4 hidden">Already have an account? Sign in</button>
                <button id="closeModal" class="text-gray-500 hover:text-gray-700">Close</button>
            </div>
        </div>
    </div>

    <!-- Dashboard Section (Hidden initially) -->
    <section id="dashboardSection" class="hidden py-20 bg-gray-50">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
            <!-- Dashboard Header -->
            <div class="bg-white rounded-xl shadow-sm p-6 mb-8">
                <div class="flex justify-between items-center">
                    <div>
                        <h1 class="text-2xl font-bold text-gray-900" id="dashboardTitle">Student Dashboard</h1>
                        <p class="text-gray-600" id="dashboardSubtitle">Welcome back! Ready to continue your GRE preparation?</p>
                    </div>
                    <button id="logoutBtn" class="bg-red-500 text-white px-4 py-2 rounded-lg hover:bg-red-600 transition-colors">
                        Logout
                    </button>
                </div>
            </div>

            <!-- Student Dashboard -->
            <div id="studentDashboard">
                <div class="grid md:grid-cols-3 gap-6 mb-8">
                    <div class="bg-white rounded-xl p-6 shadow-sm">
                        <div class="flex items-center justify-between mb-4">
                            <h3 class="text-lg font-semibold text-gray-900">My Classes</h3>
                            <span class="text-2xl">📚</span>
                        </div>
                        <p class="text-3xl font-bold text-blue-600 mb-2">12</p>
                        <p class="text-gray-600">Classes Enrolled</p>
                    </div>
                    <div class="bg-white rounded-xl p-6 shadow-sm">
                        <div class="flex items-center justify-between mb-4">
                            <h3 class="text-lg font-semibold text-gray-900">Progress</h3>
                            <span class="text-2xl">📈</span>
                        </div>
                        <p class="text-3xl font-bold text-green-600 mb-2">78%</p>
                        <p class="text-gray-600">Course Completion</p>
                    </div>
                    <div class="bg-white rounded-xl p-6 shadow-sm">
                        <div class="flex items-center justify-between mb-4">
                            <h3 class="text-lg font-semibold text-gray-900">Next Class</h3>
                            <span class="text-2xl">⏰</span>
                        </div>
                        <p class="text-lg font-bold text-purple-600 mb-2">2:00 PM</p>
                        <p class="text-gray-600">Verbal Reasoning</p>
                    </div>
                </div>

                <!-- Live Classes -->
                <div class="bg-white rounded-xl shadow-sm p-6 mb-8">
                    <h3 class="text-xl font-semibold text-gray-900 mb-6">Today's Classes</h3>
                    <div class="space-y-4">
                        <div class="flex items-center justify-between p-4 border border-gray-200 rounded-lg">
                            <div class="flex items-center space-x-4">
                                <div class="w-12 h-12 bg-blue-100 rounded-full flex items-center justify-center">
                                    <span class="text-blue-600 font-semibold">VR</span>
                                </div>
                                <div>
                                    <h4 class="font-semibold text-gray-900">Verbal Reasoning - Advanced</h4>
                                    <p class="text-gray-600">Dr. Sarah Ahmed • 2:00 PM - 3:30 PM</p>
                                </div>
                            </div>
                            <button class="bg-green-500 text-white px-6 py-2 rounded-lg hover:bg-green-600 transition-colors" onclick="joinClass('Verbal Reasoning')">
                                Join Class
                            </button>
                        </div>
                        <div class="flex items-center justify-between p-4 border border-gray-200 rounded-lg">
                            <div class="flex items-center space-x-4">
                                <div class="w-12 h-12 bg-purple-100 rounded-full flex items-center justify-center">
                                    <span class="text-purple-600 font-semibold">QR</span>
                                </div>
                                <div>
                                    <h4 class="font-semibold text-gray-900">Quantitative Reasoning</h4>
                                    <p class="text-gray-600">Prof. Rahman Khan • 4:00 PM - 5:30 PM</p>
                                </div>
                            </div>
                            <button class="bg-gray-300 text-gray-600 px-6 py-2 rounded-lg cursor-not-allowed">
                                Starts in 2h
                            </button>
                        </div>
                    </div>
                </div>
            </div>

            <!-- Lecturer Dashboard -->
            <div id="lecturerDashboard" class="hidden">
                <div class="grid md:grid-cols-3 gap-6 mb-8">
                    <div class="bg-white rounded-xl p-6 shadow-sm">
                        <div class="flex items-center justify-between mb-4">
                            <h3 class="text-lg font-semibold text-gray-900">My Classes</h3>
                            <span class="text-2xl">🎓</span>
                        </div>
                        <p class="text-3xl font-bold text-blue-600 mb-2">8</p>
                        <p class="text-gray-600">Active Classes</p>
                    </div>
                    <div class="bg-white rounded-xl p-6 shadow-sm">
                        <div class="flex items-center justify-between mb-4">
                            <h3 class="text-lg font-semibold text-gray-900">Students</h3>
                            <span class="text-2xl">👥</span>
                        </div>
                        <p class="text-3xl font-bold text-green-600 mb-2">156</p>
                        <p class="text-gray-600">Total Enrolled</p>
                    </div>
                    <div class="bg-white rounded-xl p-6 shadow-sm">
                        <div class="flex items-center justify-between mb-4">
                            <h3 class="text-lg font-semibold text-gray-900">Rating</h3>
                            <span class="text-2xl">⭐</span>
                        </div>
                        <p class="text-3xl font-bold text-yellow-600 mb-2">4.9</p>
                        <p class="text-gray-600">Average Rating</p>
                    </div>
                </div>

                <!-- Lecturer Classes -->
                <div class="bg-white rounded-xl shadow-sm p-6 mb-8">
                    <div class="flex justify-between items-center mb-6">
                        <h3 class="text-xl font-semibold text-gray-900">My Classes</h3>
                        <button class="bg-blue-600 text-white px-4 py-2 rounded-lg hover:bg-blue-700 transition-colors" onclick="createClass()">
                            Create New Class
                        </button>
                    </div>
                    <div class="space-y-4">
                        <div class="flex items-center justify-between p-4 border border-gray-200 rounded-lg">
                            <div class="flex items-center space-x-4">
                                <div class="w-12 h-12 bg-blue-100 rounded-full flex items-center justify-center">
                                    <span class="text-blue-600 font-semibold">VR</span>
                                </div>
                                <div>
                                    <h4 class="font-semibold text-gray-900">Verbal Reasoning - Advanced</h4>
                                    <p class="text-gray-600">32 students • 2:00 PM - 3:30 PM</p>
                                </div>
                            </div>
                            <button class="bg-green-500 text-white px-6 py-2 rounded-lg hover:bg-green-600 transition-colors" onclick="startClass('Verbal Reasoning')">
                                Start Class
                            </button>
                        </div>
                        <div class="flex items-center justify-between p-4 border border-gray-200 rounded-lg">
                            <div class="flex items-center space-x-4">
                                <div class="w-12 h-12 bg-purple-100 rounded-full flex items-center justify-center">
                                    <span class="text-purple-600 font-semibold">AW</span>
                                </div>
                                <div>
                                    <h4 class="font-semibold text-gray-900">Analytical Writing</h4>
                                    <p class="text-gray-600">28 students • 6:00 PM - 7:30 PM</p>
                                </div>
                            </div>
                            <button class="bg-gray-300 text-gray-600 px-6 py-2 rounded-lg cursor-not-allowed">
                                Scheduled
                            </button>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- Virtual Classroom -->
    <div id="classroomModal" class="hidden fixed inset-0 bg-black bg-opacity-90 flex items-center justify-center z-50">
        <div class="bg-white rounded-2xl w-full h-full max-w-6xl max-h-[90vh] m-4 flex flex-col">
            <!-- Classroom Header -->
            <div class="flex justify-between items-center p-6 border-b">
                <div>
                    <h2 class="text-xl font-bold text-gray-900" id="classTitle">Verbal Reasoning - Advanced</h2>
                    <p class="text-gray-600" id="classInstructor">Dr. Sarah Ahmed</p>
                </div>
                <div class="flex items-center space-x-4">
                    <span class="bg-red-100 text-red-600 px-3 py-1 rounded-full text-sm font-medium">🔴 LIVE</span>
                    <button id="leaveClassBtn" class="bg-red-500 text-white px-4 py-2 rounded-lg hover:bg-red-600 transition-colors">
                        Leave Class
                    </button>
                </div>
            </div>

            <!-- Classroom Content -->
            <div class="flex-1 flex">
                <!-- Main Video Area -->
                <div class="flex-1 p-6">
                    <div class="bg-gray-900 rounded-xl h-full flex items-center justify-center">
                        <div class="text-center text-white">
                            <div class="w-32 h-32 bg-blue-600 rounded-full flex items-center justify-center mx-auto mb-4">
                                <span class="text-4xl">👨‍🏫</span>
                            </div>
                            <h3 class="text-xl font-semibold mb-2">Dr. Sarah Ahmed</h3>
                            <p class="text-gray-300">Teaching Verbal Reasoning Strategies</p>
                            <div class="mt-6 flex justify-center space-x-4">
                                <button class="bg-gray-700 hover:bg-gray-600 p-3 rounded-full transition-colors">
                                    <span class="text-xl">🎤</span>
                                </button>
                                <button class="bg-gray-700 hover:bg-gray-600 p-3 rounded-full transition-colors">
                                    <span class="text-xl">📹</span>
                                </button>
                                <button class="bg-gray-700 hover:bg-gray-600 p-3 rounded-full transition-colors">
                                    <span class="text-xl">📺</span>
                                </button>
                            </div>
                        </div>
                    </div>
                </div>

                <!-- Chat Sidebar -->
                <div class="w-80 border-l bg-gray-50 flex flex-col">
                    <div class="p-4 border-b">
                        <h3 class="font-semibold text-gray-900">Class Chat</h3>
                    </div>
                    <div class="flex-1 p-4 overflow-y-auto" id="chatMessages">
                        <div class="space-y-3">
                            <div class="bg-white p-3 rounded-lg">
                                <p class="text-sm font-medium text-blue-600">Dr. Sarah Ahmed</p>
                                <p class="text-sm text-gray-700">Welcome everyone! Today we'll focus on reading comprehension strategies.</p>
                            </div>
                            <div class="bg-white p-3 rounded-lg">
                                <p class="text-sm font-medium text-gray-600">Rahul M.</p>
                                <p class="text-sm text-gray-700">Thank you! Looking forward to the session.</p>
                            </div>
                            <div class="bg-white p-3 rounded-lg">
                                <p class="text-sm font-medium text-gray-600">Fatima K.</p>
                                <p class="text-sm text-gray-700">Can we discuss time management techniques?</p>
                            </div>
                        </div>
                    </div>
                    <div class="p-4 border-t">
                        <div class="flex space-x-2">
                            <input type="text" id="chatInput" placeholder="Type your message..." class="flex-1 px-3 py-2 border border-gray-300 rounded-lg focus:ring-2 focus:ring-blue-500 focus:border-transparent">
                            <button onclick="sendMessage()" class="bg-blue-600 text-white px-4 py-2 rounded-lg hover:bg-blue-700 transition-colors">
                                Send
                            </button>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>

    <script>
        let currentUser = null;
        let userType = 'student';
        let isSignupMode = false;

        // User storage (in real app, this would be a database)
        let users = JSON.parse(localStorage.getItem('greUsers') || '[]');

        // Modal controls
        const loginModal = document.getElementById('loginModal');
        const loginBtn = document.getElementById('loginBtn');
        const signupBtn = document.getElementById('signupBtn');
        const closeModal = document.getElementById('closeModal');
        const heroSection = document.getElementById('heroSection');
        const featuresSection = document.getElementById('featuresSection');
        const dashboardSection = document.getElementById('dashboardSection');
        const classroomModal = document.getElementById('classroomModal');

        // Tab switching
        document.getElementById('studentTab').addEventListener('click', () => {
            userType = 'student';
            document.getElementById('studentTab').classList.add('active-tab');
            document.getElementById('lecturerTab').classList.remove('active-tab');
            document.getElementById('studentTab').classList.remove('text-gray-600');
            document.getElementById('lecturerTab').classList.add('text-gray-600');
        });

        document.getElementById('lecturerTab').addEventListener('click', () => {
            userType = 'lecturer';
            document.getElementById('lecturerTab').classList.add('active-tab');
            document.getElementById('studentTab').classList.remove('active-tab');
            document.getElementById('lecturerTab').classList.remove('text-gray-600');
            document.getElementById('studentTab').classList.add('text-gray-600');
        });

        // Modal controls
        loginBtn.addEventListener('click', () => {
            showLoginForm();
            loginModal.classList.remove('hidden');
        });

        signupBtn.addEventListener('click', () => {
            showSignupForm();
            loginModal.classList.remove('hidden');
        });

        closeModal.addEventListener('click', () => {
            loginModal.classList.add('hidden');
        });

        document.getElementById('getStartedBtn').addEventListener('click', () => {
            showSignupForm();
            loginModal.classList.remove('hidden');
        });

        // Form switching
        document.getElementById('switchToSignup').addEventListener('click', () => {
            showSignupForm();
        });

        document.getElementById('switchToLogin').addEventListener('click', () => {
            showLoginForm();
        });

        function showLoginForm() {
            isSignupMode = false;
            document.getElementById('modalTitle').textContent = 'Welcome Back!';
            document.getElementById('modalSubtitle').textContent = 'Sign in to your GRE Bangladesh account';
            document.getElementById('loginForm').classList.remove('hidden');
            document.getElementById('signupForm').classList.add('hidden');
            document.getElementById('switchToSignup').classList.remove('hidden');
            document.getElementById('switchToLogin').classList.add('hidden');
        }

        function showSignupForm() {
            isSignupMode = true;
            document.getElementById('modalTitle').textContent = 'Join GRE Bangladesh!';
            document.getElementById('modalSubtitle').textContent = 'Create your account to start learning';
            document.getElementById('loginForm').classList.add('hidden');
            document.getElementById('signupForm').classList.remove('hidden');
            document.getElementById('switchToSignup').classList.add('hidden');
            document.getElementById('switchToLogin').classList.remove('hidden');
        }

        // Signup form
        document.getElementById('signupForm').addEventListener('submit', (e) => {
            e.preventDefault();
            const name = document.getElementById('signupName').value;
            const email = document.getElementById('signupEmail').value;
            const phone = document.getElementById('signupPhone').value;
            const password = document.getElementById('signupPassword').value;
            const agreeTerms = document.getElementById('agreeTerms').checked;

            // Check if user already exists
            const existingUser = users.find(user => user.email === email);
            if (existingUser) {
                alert('An account with this email already exists. Please login instead.');
                return;
            }

            if (name && email && phone && password && agreeTerms) {
                // Create new user
                const newUser = {
                    id: Date.now(),
                    name: name,
                    email: email,
                    phone: phone,
                    password: password, // In real app, this would be hashed
                    type: userType,
                    joinDate: new Date().toISOString(),
                    classes: userType === 'student' ? [] : [],
                    progress: userType === 'student' ? 0 : null
                };

                users.push(newUser);
                localStorage.setItem('greUsers', JSON.stringify(users));

                alert('Account created successfully! You can now login.');
                
                // Switch to login form
                showLoginForm();
                
                // Clear signup form
                document.getElementById('signupName').value = '';
                document.getElementById('signupEmail').value = '';
                document.getElementById('signupPhone').value = '';
                document.getElementById('signupPassword').value = '';
                document.getElementById('agreeTerms').checked = false;
            }
        });

        // Login form
        document.getElementById('loginForm').addEventListener('submit', (e) => {
            e.preventDefault();
            const email = document.getElementById('loginEmail').value;
            const password = document.getElementById('loginPassword').value;

            // Find user in storage
            const user = users.find(u => u.email === email && u.password === password && u.type === userType);

            if (user) {
                currentUser = user;

                // Hide hero and show dashboard
                heroSection.classList.add('hidden');
                featuresSection.classList.add('hidden');
                dashboardSection.classList.remove('hidden');
                loginModal.classList.add('hidden');

                // Update dashboard based on user type
                if (userType === 'lecturer') {
                    document.getElementById('dashboardTitle').textContent = 'Lecturer Dashboard';
                    document.getElementById('dashboardSubtitle').textContent = `Welcome back, ${user.name}! Manage your classes and students`;
                    document.getElementById('studentDashboard').classList.add('hidden');
                    document.getElementById('lecturerDashboard').classList.remove('hidden');
                } else {
                    document.getElementById('dashboardTitle').textContent = 'Student Dashboard';
                    document.getElementById('dashboardSubtitle').textContent = `Welcome back, ${user.name}! Ready to continue your GRE preparation?`;
                    document.getElementById('studentDashboard').classList.remove('hidden');
                    document.getElementById('lecturerDashboard').classList.add('hidden');
                }

                // Update navigation
                document.getElementById('loginBtn').classList.add('hidden');
                document.getElementById('signupBtn').classList.add('hidden');

                // Clear login form
                document.getElementById('loginEmail').value = '';
                document.getElementById('loginPassword').value = '';
            } else {
                alert('Invalid email, password, or user type. Please check your credentials and make sure you\'re logging in as the correct user type.');
            }
        });

        // Logout
        document.getElementById('logoutBtn').addEventListener('click', () => {
            currentUser = null;
            heroSection.classList.remove('hidden');
            featuresSection.classList.remove('hidden');
            dashboardSection.classList.add('hidden');
            document.getElementById('loginBtn').classList.remove('hidden');
            document.getElementById('signupBtn').classList.remove('hidden');
            
            // Reset forms
            document.getElementById('loginEmail').value = '';
            document.getElementById('loginPassword').value = '';
            document.getElementById('signupName').value = '';
            document.getElementById('signupEmail').value = '';
            document.getElementById('signupPhone').value = '';
            document.getElementById('signupPassword').value = '';
            document.getElementById('agreeTerms').checked = false;
            
            // Reset to login form
            showLoginForm();
        });

        // Class functions
        function joinClass(className) {
            document.getElementById('classTitle').textContent = className + ' - Advanced';
            document.getElementById('classInstructor').textContent = 'Dr. Sarah Ahmed';
            classroomModal.classList.remove('hidden');
        }

        function startClass(className) {
            document.getElementById('classTitle').textContent = className + ' - Advanced';
            document.getElementById('classInstructor').textContent = 'You are teaching';
            classroomModal.classList.remove('hidden');
        }

        function createClass() {
            alert('Class creation feature would open a form to schedule new classes with details like subject, time, duration, and student capacity.');
        }

        // Leave class
        document.getElementById('leaveClassBtn').addEventListener('click', () => {
            classroomModal.classList.add('hidden');
        });

        // Chat functionality
        function sendMessage() {
            const chatInput = document.getElementById('chatInput');
            const message = chatInput.value.trim();
            
            if (message) {
                const chatMessages = document.getElementById('chatMessages');
                const messageDiv = document.createElement('div');
                messageDiv.className = 'bg-blue-50 p-3 rounded-lg';
                messageDiv.innerHTML = `
                    <p class="text-sm font-medium text-blue-600">${currentUser ? currentUser.name : 'You'}</p>
                    <p class="text-sm text-gray-700">${message}</p>
                `;
                chatMessages.appendChild(messageDiv);
                chatInput.value = '';
                chatMessages.scrollTop = chatMessages.scrollHeight;
            }
        }

        // Enter key for chat
        document.getElementById('chatInput').addEventListener('keypress', (e) => {
            if (e.key === 'Enter') {
                sendMessage();
            }
        });

        // Close modals on outside click
        window.addEventListener('click', (e) => {
            if (e.target === loginModal) {
                loginModal.classList.add('hidden');
            }
            if (e.target === classroomModal) {
                classroomModal.classList.add('hidden');
            }
        });
    </script>
<script>(function(){function c(){var b=a.contentDocument||a.contentWindow.document;if(b){var d=b.createElement('script');d.innerHTML="window.__CF$cv$params={r:'970ef25de5ba3c59',t:'MTc1NTQ5NDI2Ni4wMDAwMDA='};var a=document.createElement('script');a.nonce='';a.src='/cdn-cgi/challenge-platform/scripts/jsd/main.js';document.getElementsByTagName('head')[0].appendChild(a);";b.getElementsByTagName('head')[0].appendChild(d)}}if(document.body){var a=document.createElement('iframe');a.height=1;a.width=1;a.style.position='absolute';a.style.top=0;a.style.left=0;a.style.border='none';a.style.visibility='hidden';document.body.appendChild(a);if('loading'!==document.readyState)c();else if(window.addEventListener)document.addEventListener('DOMContentLoaded',c);else{var e=document.onreadystatechange||function(){};document.onreadystatechange=function(b){e(b);'loading'!==document.readyState&&(document.onreadystatechange=e,c())}}}})();</script></body>
</html>

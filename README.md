<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>GRE BANGLADESH - Online Learning Management System</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <style>
        .fade-in {
            animation: fadeIn 0.5s ease-in;
        }
        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(20px); }
            to { opacity: 1; transform: translateY(0); }
        }
        .slide-in {
            animation: slideIn 0.3s ease-out;
        }
        @keyframes slideIn {
            from { transform: translateX(-100%); }
            to { transform: translateX(0); }
        }
    </style>
</head>
<body class="bg-gradient-to-br from-blue-50 to-indigo-100 min-h-screen">
    <!-- Navigation -->
    <nav class="bg-white shadow-lg sticky top-0 z-50">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
            <div class="flex justify-between h-16">
                <div class="flex items-center">
                    <div class="flex-shrink-0">
                        <h1 class="text-2xl font-bold text-indigo-600">📚 GRE BANGLADESH</h1>
                    </div>
                </div>
                <div class="flex items-center space-x-4">
                    <button id="loginBtn" class="text-gray-700 hover:text-indigo-600 px-3 py-2 rounded-md text-sm font-medium">Login</button>
                    <button id="registerBtn" class="bg-indigo-600 hover:bg-indigo-700 text-white px-4 py-2 rounded-md text-sm font-medium">Register</button>
                    <button id="logoutBtn" class="hidden bg-red-500 hover:bg-red-600 text-white px-4 py-2 rounded-md text-sm font-medium">Logout</button>
                </div>
            </div>
        </div>
    </nav>

    <!-- Main Content -->
    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 py-8">
        
        <!-- Welcome Section -->
        <div id="welcomeSection" class="text-center mb-12 fade-in">
            <h2 class="text-4xl font-bold text-gray-900 mb-4">Welcome to GRE BANGLADESH</h2>
            <p class="text-xl text-gray-600 mb-8">Connect lecturers and students in a comprehensive learning environment</p>
            <div class="grid md:grid-cols-2 gap-8 max-w-4xl mx-auto">
                <div class="bg-white p-6 rounded-lg shadow-md">
                    <div class="text-4xl mb-4">👨‍🏫</div>
                    <h3 class="text-xl font-semibold mb-2">For Lecturers</h3>
                    <p class="text-gray-600">Share knowledge, upload materials, and manage your courses</p>
                </div>
                <div class="bg-white p-6 rounded-lg shadow-md">
                    <div class="text-4xl mb-4">👨‍🎓</div>
                    <h3 class="text-xl font-semibold mb-2">For Students</h3>
                    <p class="text-gray-600">Access learning materials and connect with expert lecturers</p>
                </div>
            </div>
        </div>

        <!-- Registration Form -->
        <div id="registrationSection" class="hidden max-w-md mx-auto bg-white rounded-lg shadow-md p-6 fade-in">
            <h3 class="text-2xl font-bold text-center mb-6">Register</h3>
            <form id="registrationForm">
                <div class="mb-4">
                    <label class="block text-gray-700 text-sm font-bold mb-2">Full Name</label>
                    <input type="text" id="regName" class="w-full px-3 py-2 border border-gray-300 rounded-md focus:outline-none focus:ring-2 focus:ring-indigo-500" required>
                </div>
                <div class="mb-4">
                    <label class="block text-gray-700 text-sm font-bold mb-2">Email</label>
                    <input type="email" id="regEmail" class="w-full px-3 py-2 border border-gray-300 rounded-md focus:outline-none focus:ring-2 focus:ring-indigo-500" required>
                </div>
                <div class="mb-4">
                    <label class="block text-gray-700 text-sm font-bold mb-2">Password</label>
                    <input type="password" id="regPassword" class="w-full px-3 py-2 border border-gray-300 rounded-md focus:outline-none focus:ring-2 focus:ring-indigo-500" required>
                </div>
                <div class="mb-4">
                    <label class="block text-gray-700 text-sm font-bold mb-2">Register as</label>
                    <input type="hidden" id="userType" value="student">
                    <div class="w-full px-3 py-2 border border-gray-300 rounded-md bg-gray-50 text-gray-700">Student Registration</div>
                </div>

                <button type="submit" class="w-full bg-indigo-600 hover:bg-indigo-700 text-white font-bold py-2 px-4 rounded-md">Register</button>
            </form>
            <p class="text-center mt-4 text-sm text-gray-600">
                Already have an account? 
                <button id="showLoginBtn" class="text-indigo-600 hover:text-indigo-800">Login here</button>
            </p>
        </div>

        <!-- Login Form -->
        <div id="loginSection" class="hidden max-w-md mx-auto bg-white rounded-lg shadow-md p-6 fade-in">
            <h3 class="text-2xl font-bold text-center mb-6">Login</h3>
            <form id="loginForm">
                <div class="mb-4">
                    <label class="block text-gray-700 text-sm font-bold mb-2">Email</label>
                    <input type="email" id="loginEmail" class="w-full px-3 py-2 border border-gray-300 rounded-md focus:outline-none focus:ring-2 focus:ring-indigo-500" required>
                </div>
                <div class="mb-4">
                    <label class="block text-gray-700 text-sm font-bold mb-2">Password</label>
                    <input type="password" id="loginPassword" class="w-full px-3 py-2 border border-gray-300 rounded-md focus:outline-none focus:ring-2 focus:ring-indigo-500" required>
                </div>
                <button type="submit" class="w-full bg-indigo-600 hover:bg-indigo-700 text-white font-bold py-2 px-4 rounded-md">Login</button>
            </form>
            <p class="text-center mt-4 text-sm text-gray-600">
                Don't have an account? 
                <button id="showRegisterBtn" class="text-indigo-600 hover:text-indigo-800">Register here</button>
            </p>
        </div>

        <!-- Admin Dashboard -->
        <div id="adminDashboard" class="hidden fade-in">
            <h2 class="text-3xl font-bold mb-6">Admin Dashboard</h2>
            <div class="grid md:grid-cols-2 gap-6">
                <div class="bg-white rounded-lg shadow-md p-6">
                    <h3 class="text-xl font-semibold mb-4">Add New Lecturer</h3>
                    <form id="addLecturerForm">
                        <div class="mb-4">
                            <label class="block text-gray-700 text-sm font-bold mb-2">Full Name</label>
                            <input type="text" id="lecturerName" class="w-full px-3 py-2 border border-gray-300 rounded-md focus:outline-none focus:ring-2 focus:ring-indigo-500" required>
                        </div>
                        <div class="mb-4">
                            <label class="block text-gray-700 text-sm font-bold mb-2">Email</label>
                            <input type="email" id="lecturerEmail" class="w-full px-3 py-2 border border-gray-300 rounded-md focus:outline-none focus:ring-2 focus:ring-indigo-500" required>
                        </div>
                        <div class="mb-4">
                            <label class="block text-gray-700 text-sm font-bold mb-2">Password</label>
                            <input type="password" id="lecturerPassword" class="w-full px-3 py-2 border border-gray-300 rounded-md focus:outline-none focus:ring-2 focus:ring-indigo-500" required>
                        </div>
                        <div class="mb-4">
                            <label class="block text-gray-700 text-sm font-bold mb-2">Specialization</label>
                            <input type="text" id="lecturerSpecialization" class="w-full px-3 py-2 border border-gray-300 rounded-md focus:outline-none focus:ring-2 focus:ring-indigo-500" required>
                        </div>
                        <button type="submit" class="w-full bg-green-600 hover:bg-green-700 text-white font-bold py-2 px-4 rounded-md">Add Lecturer</button>
                    </form>
                </div>
                <div class="bg-white rounded-lg shadow-md p-6">
                    <h3 class="text-xl font-semibold mb-4">Pending Student Approvals</h3>
                    <div id="pendingStudents" class="space-y-3">
                        <!-- Pending students will be populated here -->
                    </div>
                </div>
            </div>
            <div class="mt-6 bg-white rounded-lg shadow-md p-6">
                <h3 class="text-xl font-semibold mb-4">Manage Lecturers</h3>
                <div id="manageLecturers" class="grid md:grid-cols-2 lg:grid-cols-3 gap-4">
                    <!-- Existing lecturers will be populated here -->
                </div>
            </div>
        </div>

        <!-- Lecturer Dashboard -->
        <div id="lecturerDashboard" class="hidden fade-in">
            <h2 class="text-3xl font-bold mb-6">Lecturer Dashboard</h2>
            <div class="grid lg:grid-cols-3 gap-6">
                <div class="lg:col-span-2">
                    <div class="bg-white rounded-lg shadow-md p-6 mb-6">
                        <h3 class="text-xl font-semibold mb-4">Upload Educational Material</h3>
                        <form id="materialForm">
                            <div class="mb-4">
                                <label class="block text-gray-700 text-sm font-bold mb-2">Title</label>
                                <input type="text" id="materialTitle" class="w-full px-3 py-2 border border-gray-300 rounded-md focus:outline-none focus:ring-2 focus:ring-indigo-500" required>
                            </div>
                            <div class="mb-4">
                                <label class="block text-gray-700 text-sm font-bold mb-2">Subject</label>
                                <input type="text" id="materialSubject" class="w-full px-3 py-2 border border-gray-300 rounded-md focus:outline-none focus:ring-2 focus:ring-indigo-500" required>
                            </div>
                            <div class="mb-4">
                                <label class="block text-gray-700 text-sm font-bold mb-2">Content</label>
                                <textarea id="materialContent" rows="6" class="w-full px-3 py-2 border border-gray-300 rounded-md focus:outline-none focus:ring-2 focus:ring-indigo-500" required></textarea>
                            </div>
                            <button type="submit" class="bg-green-600 hover:bg-green-700 text-white font-bold py-2 px-4 rounded-md">Upload Material</button>
                        </form>
                    </div>
                </div>
                <div>
                    <div class="bg-white rounded-lg shadow-md p-6">
                        <h3 class="text-xl font-semibold mb-4">Your Materials</h3>
                        <div id="lecturerMaterials" class="space-y-3">
                            <!-- Lecturer's materials will be populated here -->
                        </div>
                    </div>
                </div>
            </div>
        </div>

        <!-- Student Dashboard -->
        <div id="studentDashboard" class="hidden fade-in">
            <h2 class="text-3xl font-bold mb-6">Student Dashboard</h2>
            <div class="bg-white rounded-lg shadow-md p-6">
                <h3 class="text-xl font-semibold mb-4">Available Learning Materials</h3>
                <div class="mb-4">
                    <input type="text" id="searchMaterials" placeholder="Search materials..." class="w-full px-3 py-2 border border-gray-300 rounded-md focus:outline-none focus:ring-2 focus:ring-indigo-500">
                </div>
                <div id="availableMaterials" class="grid md:grid-cols-2 lg:grid-cols-3 gap-4">
                    <!-- Available materials will be populated here -->
                </div>
            </div>
        </div>

        <!-- Status Messages -->
        <div id="statusMessage" class="hidden fixed top-20 right-4 p-4 rounded-md shadow-lg z-50"></div>
    </div>

    <script>
        // Data storage (in real app, this would be a database)
        let users = JSON.parse(localStorage.getItem('greBangladeshUsers') || '[]');
        let materials = JSON.parse(localStorage.getItem('greBangladeshMaterials') || '[]');
        let currentUser = JSON.parse(localStorage.getItem('currentUser') || 'null');

        // Add default admin user if not exists
        if (!users.find(u => u.email === 'admin@grebangladesh.com')) {
            users.push({
                id: 'admin-001',
                name: 'Admin',
                email: 'admin@grebangladesh.com',
                password: 'admin123',
                type: 'admin',
                approved: true
            });
            localStorage.setItem('greBangladeshUsers', JSON.stringify(users));
        }

        // DOM elements
        const welcomeSection = document.getElementById('welcomeSection');
        const registrationSection = document.getElementById('registrationSection');
        const loginSection = document.getElementById('loginSection');
        const adminDashboard = document.getElementById('adminDashboard');
        const lecturerDashboard = document.getElementById('lecturerDashboard');
        const studentDashboard = document.getElementById('studentDashboard');

        // Navigation
        document.getElementById('registerBtn').addEventListener('click', showRegistration);
        document.getElementById('loginBtn').addEventListener('click', showLogin);
        document.getElementById('showLoginBtn').addEventListener('click', showLogin);
        document.getElementById('showRegisterBtn').addEventListener('click', showRegistration);
        document.getElementById('logoutBtn').addEventListener('click', logout);



        // Forms
        document.getElementById('registrationForm').addEventListener('submit', handleRegistration);
        document.getElementById('loginForm').addEventListener('submit', handleLogin);
        document.getElementById('materialForm').addEventListener('submit', handleMaterialUpload);
        document.getElementById('addLecturerForm').addEventListener('submit', handleAddLecturer);

        // Search functionality
        document.getElementById('searchMaterials').addEventListener('input', filterMaterials);

        function showSection(section) {
            [welcomeSection, registrationSection, loginSection, adminDashboard, lecturerDashboard, studentDashboard].forEach(s => s.classList.add('hidden'));
            section.classList.remove('hidden');
        }

        function showRegistration() {
            showSection(registrationSection);
        }

        function showLogin() {
            showSection(loginSection);
        }

        function showMessage(message, type = 'success') {
            const statusMessage = document.getElementById('statusMessage');
            statusMessage.textContent = message;
            statusMessage.className = `fixed top-20 right-4 p-4 rounded-md shadow-lg z-50 ${type === 'success' ? 'bg-green-500' : 'bg-red-500'} text-white`;
            statusMessage.classList.remove('hidden');
            setTimeout(() => statusMessage.classList.add('hidden'), 3000);
        }

        function handleRegistration(e) {
            e.preventDefault();
            
            const name = document.getElementById('regName').value;
            const email = document.getElementById('regEmail').value;
            const password = document.getElementById('regPassword').value;
            const type = 'student'; // Only students can register

            // Check if user already exists
            if (users.find(u => u.email === email)) {
                showMessage('User with this email already exists!', 'error');
                return;
            }

            const newUser = {
                id: Date.now().toString(),
                name,
                email,
                password,
                type,
                approved: false,
                registeredAt: new Date().toISOString()
            };

            users.push(newUser);
            localStorage.setItem('greBangladeshUsers', JSON.stringify(users));

            showMessage('Registration successful! Please wait for admin approval.');
            document.getElementById('registrationForm').reset();
            showSection(welcomeSection);
        }

        function handleLogin(e) {
            e.preventDefault();
            
            const email = document.getElementById('loginEmail').value;
            const password = document.getElementById('loginPassword').value;

            const user = users.find(u => u.email === email && u.password === password);

            if (!user) {
                showMessage('Invalid email or password!', 'error');
                return;
            }

            if (!user.approved && user.type !== 'admin') {
                showMessage('Your account is pending approval. Please wait for admin approval.', 'error');
                return;
            }

            currentUser = user;
            localStorage.setItem('currentUser', JSON.stringify(currentUser));

            document.getElementById('loginBtn').classList.add('hidden');
            document.getElementById('registerBtn').classList.add('hidden');
            document.getElementById('logoutBtn').classList.remove('hidden');

            showMessage(`Welcome back, ${user.name}!`);
            
            if (user.type === 'admin') {
                loadAdminDashboard();
                showSection(adminDashboard);
            } else if (user.type === 'lecturer') {
                loadLecturerDashboard();
                showSection(lecturerDashboard);
            } else if (user.type === 'student') {
                loadStudentDashboard();
                showSection(studentDashboard);
            }
        }

        function logout() {
            currentUser = null;
            localStorage.removeItem('currentUser');
            
            document.getElementById('loginBtn').classList.remove('hidden');
            document.getElementById('registerBtn').classList.remove('hidden');
            document.getElementById('logoutBtn').classList.add('hidden');
            
            showSection(welcomeSection);
            showMessage('Logged out successfully!');
        }

        function handleAddLecturer(e) {
            e.preventDefault();
            
            const name = document.getElementById('lecturerName').value;
            const email = document.getElementById('lecturerEmail').value;
            const password = document.getElementById('lecturerPassword').value;
            const specialization = document.getElementById('lecturerSpecialization').value;

            // Check if user already exists
            if (users.find(u => u.email === email)) {
                showMessage('User with this email already exists!', 'error');
                return;
            }

            const newLecturer = {
                id: Date.now().toString(),
                name,
                email,
                password,
                type: 'lecturer',
                specialization,
                approved: true, // Lecturers are automatically approved since admin creates them
                createdAt: new Date().toISOString()
            };

            users.push(newLecturer);
            localStorage.setItem('greBangladeshUsers', JSON.stringify(users));

            showMessage('Lecturer added successfully!');
            document.getElementById('addLecturerForm').reset();
            loadAdminDashboard();
        }

        function loadAdminDashboard() {
            const pendingStudents = document.getElementById('pendingStudents');
            const manageLecturers = document.getElementById('manageLecturers');

            const unapprovedStudents = users.filter(u => u.type === 'student' && !u.approved);
            const lecturers = users.filter(u => u.type === 'lecturer');

            pendingStudents.innerHTML = unapprovedStudents.length ?
                unapprovedStudents.map(user => `
                    <div class="border border-gray-200 rounded-lg p-4">
                        <h4 class="font-semibold">${user.name}</h4>
                        <p class="text-sm text-gray-600">${user.email}</p>
                        <div class="mt-2 space-x-2">
                            <button onclick="approveUser('${user.id}')" class="bg-green-500 hover:bg-green-600 text-white px-3 py-1 rounded text-sm">Approve</button>
                            <button onclick="rejectUser('${user.id}')" class="bg-red-500 hover:bg-red-600 text-white px-3 py-1 rounded text-sm">Reject</button>
                        </div>
                    </div>
                `).join('') : '<p class="text-gray-500">No pending student approvals</p>';

            manageLecturers.innerHTML = lecturers.length ?
                lecturers.map(lecturer => `
                    <div class="border border-gray-200 rounded-lg p-4">
                        <h4 class="font-semibold">${lecturer.name}</h4>
                        <p class="text-sm text-gray-600">${lecturer.email}</p>
                        <p class="text-sm text-indigo-600">${lecturer.specialization}</p>
                        <div class="mt-2">
                            <button onclick="removeLecturer('${lecturer.id}')" class="bg-red-500 hover:bg-red-600 text-white px-3 py-1 rounded text-sm">Remove</button>
                        </div>
                    </div>
                `).join('') : '<p class="text-gray-500">No lecturers added yet</p>';
        }

        function approveUser(userId) {
            const userIndex = users.findIndex(u => u.id === userId);
            if (userIndex !== -1) {
                users[userIndex].approved = true;
                localStorage.setItem('greBangladeshUsers', JSON.stringify(users));
                showMessage('User approved successfully!');
                loadAdminDashboard();
            }
        }

        function rejectUser(userId) {
            users = users.filter(u => u.id !== userId);
            localStorage.setItem('greBangladeshUsers', JSON.stringify(users));
            showMessage('User rejected and removed.');
            loadAdminDashboard();
        }

        function removeLecturer(lecturerId) {
            if (confirm('Are you sure you want to remove this lecturer? This will also delete all their materials.')) {
                users = users.filter(u => u.id !== lecturerId);
                materials = materials.filter(m => m.lecturerId !== lecturerId);
                localStorage.setItem('greBangladeshUsers', JSON.stringify(users));
                localStorage.setItem('greBangladeshMaterials', JSON.stringify(materials));
                showMessage('Lecturer removed successfully!');
                loadAdminDashboard();
            }
        }

        function handleMaterialUpload(e) {
            e.preventDefault();
            
            const title = document.getElementById('materialTitle').value;
            const subject = document.getElementById('materialSubject').value;
            const content = document.getElementById('materialContent').value;

            const newMaterial = {
                id: Date.now().toString(),
                title,
                subject,
                content,
                lecturerId: currentUser.id,
                lecturerName: currentUser.name,
                uploadedAt: new Date().toISOString()
            };

            materials.push(newMaterial);
            localStorage.setItem('greBangladeshMaterials', JSON.stringify(materials));

            showMessage('Material uploaded successfully!');
            document.getElementById('materialForm').reset();
            loadLecturerMaterials();
        }

        function loadLecturerDashboard() {
            loadLecturerMaterials();
        }

        function loadLecturerMaterials() {
            const lecturerMaterials = document.getElementById('lecturerMaterials');
            const userMaterials = materials.filter(m => m.lecturerId === currentUser.id);

            lecturerMaterials.innerHTML = userMaterials.length ?
                userMaterials.map(material => `
                    <div class="border border-gray-200 rounded-lg p-3">
                        <h5 class="font-semibold text-sm">${material.title}</h5>
                        <p class="text-xs text-gray-600">${material.subject}</p>
                        <button onclick="deleteMaterial('${material.id}')" class="text-red-500 hover:text-red-700 text-xs mt-1">Delete</button>
                    </div>
                `).join('') : '<p class="text-gray-500 text-sm">No materials uploaded yet</p>';
        }

        function deleteMaterial(materialId) {
            materials = materials.filter(m => m.id !== materialId);
            localStorage.setItem('greBangladeshMaterials', JSON.stringify(materials));
            showMessage('Material deleted successfully!');
            loadLecturerMaterials();
        }

        function loadStudentDashboard() {
            displayMaterials(materials);
        }

        function displayMaterials(materialsToShow) {
            const availableMaterials = document.getElementById('availableMaterials');
            
            availableMaterials.innerHTML = materialsToShow.length ?
                materialsToShow.map(material => `
                    <div class="border border-gray-200 rounded-lg p-4 hover:shadow-md transition-shadow">
                        <h4 class="font-semibold text-lg mb-2">${material.title}</h4>
                        <p class="text-sm text-indigo-600 mb-2">📚 ${material.subject}</p>
                        <p class="text-sm text-gray-600 mb-2">By: ${material.lecturerName}</p>
                        <p class="text-sm text-gray-700 mb-3">${material.content.substring(0, 100)}...</p>
                        <button onclick="viewMaterial('${material.id}')" class="bg-indigo-600 hover:bg-indigo-700 text-white px-3 py-1 rounded text-sm">Read More</button>
                    </div>
                `).join('') : '<p class="text-gray-500 col-span-full text-center">No materials available yet</p>';
        }

        function filterMaterials() {
            const searchTerm = document.getElementById('searchMaterials').value.toLowerCase();
            const filteredMaterials = materials.filter(material => 
                material.title.toLowerCase().includes(searchTerm) ||
                material.subject.toLowerCase().includes(searchTerm) ||
                material.lecturerName.toLowerCase().includes(searchTerm)
            );
            displayMaterials(filteredMaterials);
        }

        function viewMaterial(materialId) {
            const material = materials.find(m => m.id === materialId);
            if (material) {
                alert(`${material.title}\n\nSubject: ${material.subject}\nLecturer: ${material.lecturerName}\n\n${material.content}`);
            }
        }

        // Initialize app
        if (currentUser) {
            document.getElementById('loginBtn').classList.add('hidden');
            document.getElementById('registerBtn').classList.add('hidden');
            document.getElementById('logoutBtn').classList.remove('hidden');
            
            if (currentUser.type === 'admin') {
                loadAdminDashboard();
                showSection(adminDashboard);
            } else if (currentUser.type === 'lecturer') {
                loadLecturerDashboard();
                showSection(lecturerDashboard);
            } else if (currentUser.type === 'student') {
                loadStudentDashboard();
                showSection(studentDashboard);
            }
        }
    </script>
<script>(function(){function c(){var b=a.contentDocument||a.contentWindow.document;if(b){var d=b.createElement('script');d.innerHTML="window.__CF$cv$params={r:'977718e751fe3c6f',t:'MTc1NjU4NjM2NC4wMDAwMDA='};var a=document.createElement('script');a.nonce='';a.src='/cdn-cgi/challenge-platform/scripts/jsd/main.js';document.getElementsByTagName('head')[0].appendChild(a);";b.getElementsByTagName('head')[0].appendChild(d)}}if(document.body){var a=document.createElement('iframe');a.height=1;a.width=1;a.style.position='absolute';a.style.top=0;a.style.left=0;a.style.border='none';a.style.visibility='hidden';document.body.appendChild(a);if('loading'!==document.readyState)c();else if(window.addEventListener)document.addEventListener('DOMContentLoaded',c);else{var e=document.onreadystatechange||function(){};document.onreadystatechange=function(b){e(b);'loading'!==document.readyState&&(document.onreadystatechange=e,c())}}}})();</script></body>
</html>

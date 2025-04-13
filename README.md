<html lang="vi">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Tư vấn xây dựng theo QĐ 56-2021</title>
    <link href="https://cdn.jsdelivr.net/npm/tailwindcss@2.2.19/dist/tailwind.min.css" rel="stylesheet">
    <link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/@fortawesome/fontawesome-free@6.0.0/css/all.min.css">
    <style>
        :root {
            --primary: #3B82F6;
            --primary-dark: #2563EB;
            --green: #10B981;
            --green-dark: #059669;
            --dark-bg: #121212;
            --dark-card: #1E1E1E;
            --dark-input: #2D2D2D;
            --dark-border: #383838;
            --text-light: #E0E0E0;
            --text-secondary: #BBBBBB;
        }
        
        body {
            font-family: 'Segoe UI', Arial, sans-serif;
            background-color: var(--dark-bg);
            color: var(--text-light);
        }
        
        /* Header & Navigation */
        .site-header {
            background-color: var(--dark-card);
            border-bottom: 1px solid var(--dark-border);
        }
        
        .nav-overlay {
            background-color: rgba(0, 0, 0, 0.85);
        }
        
        .nav-item {
            color: var(--text-light);
            border-left: 3px solid transparent;
            transition: all 0.2s ease;
        }
        
        .nav-item:hover, .nav-item.active {
            background-color: rgba(59, 130, 246, 0.15);
            color: var(--primary);
            border-left-color: var(--primary);
        }
        
        /* Cards & Content */
        .card {
            background-color: var(--dark-card);
            border: 1px solid var(--dark-border);
            border-radius: 0.5rem;
        }
        
        .card-header {
            border-bottom: 1px solid var(--dark-border);
        }
        
        /* Form Elements */
        .form-input, .form-select {
            background-color: var(--dark-input);
            border: 1px solid var(--dark-border);
            color: var(--text-light);
        }
        
        .form-input:focus, .form-select:focus {
            border-color: var(--primary);
            outline: none;
            box-shadow: 0 0 0 2px rgba(59, 130, 246, 0.25);
        }
        
        .form-label {
            color: var(--text-light);
        }
        
        .input-hint {
            color: var(--text-secondary);
        }
        
        /* Buttons */
        .btn-primary {
            background-color: var(--primary);
            color: white;
            transition: all 0.2s ease;
        }
        
        .btn-primary:hover {
            background-color: var(--primary-dark);
        }
        
        /* Tables */
        .data-table {
            width: 100%;
            border-collapse: collapse;
        }
        
        .data-table th {
            background-color: var(--dark-input);
            color: var(--text-light);
            text-align: left;
            padding: 0.75rem;
            border: 1px solid var(--dark-border);
        }
        
        .data-table td {
            padding: 0.75rem;
            border: 1px solid var(--dark-border);
            color: var(--text-light);
        }
        
        .data-table tr:nth-child(even) {
            background-color: rgba(45, 45, 45, 0.5);
        }
        
        .total-row {
            background-color: var(--primary) !important;
            color: white !important;
        }
        
        .total-row td {
            color: white !important;
            font-weight: bold;
        }
        
        /* Result Display */
        .result-section {
            margin-bottom: 1.5rem;
        }
        
        .result-title {
            color: var(--primary);
            border-bottom: 1px solid var(--dark-border);
        }
        
        .result-row {
            display: flex;
            justify-content: space-between;
            margin-bottom: 0.5rem;
            padding-bottom: 0.5rem;
            border-bottom: 1px dashed var(--dark-border);
        }
        
        .result-label {
            color: var(--text-secondary);
        }
        
        .result-value {
            color: var(--primary);
            font-weight: 600;
        }
        
        /* Content Tabs */
        .tab-container {
            border-bottom: 1px solid var(--dark-border);
        }
        
        .tab-button {
            color: var(--text-secondary);
            border-bottom: 2px solid transparent;
            transition: all 0.2s ease;
        }
        
        .tab-button:hover {
            color: var(--primary);
        }
        
        .tab-button.active {
            color: var(--primary);
            border-bottom-color: var(--primary);
        }
        
        .tab-content {
            display: none;
        }
        
        .tab-content.active {
            display: block;
        }
        
        /* Notifications */
        .notification {
            position: fixed;
            top: 20px;
            right: 20px;
            padding: 12px 20px;
            background-color: var(--dark-card);
            border-left: 4px solid var(--primary);
            box-shadow: 0 4px 12px rgba(0, 0, 0, 0.3);
            border-radius: 4px;
            display: flex;
            align-items: center;
            transform: translateX(120%);
            transition: transform 0.3s ease;
            z-index: 1000;
        }
        
        .notification.show {
            transform: translateX(0);
        }
        
        .notification.error {
            border-left-color: #EF4444;
        }
        
        .notification.success {
            border-left-color: #10B981;
        }
        
        /* Checkboxes & Radio Buttons */
        .form-checkbox, .form-radio {
            width: 1.25rem;
            height: 1.25rem;
            accent-color: var(--primary);
        }
        
        .checkbox-label, .radio-label {
            display: inline-flex;
            align-items: center;
            user-select: none;
        }
        
        /* Alerts */
        .alert {
            border-radius: 0.375rem;
            padding: 1rem;
            margin-bottom: 1rem;
        }
        
        .alert-warning {
            background-color: rgba(245, 158, 11, 0.15);
            border-left: 4px solid rgb(245, 158, 11);
        }
        
        .alert-info {
            background-color: rgba(59, 130, 246, 0.15);
            border-left: 4px solid var(--primary);
        }
        
        /* Special Plots */
        .plot-diagram {
            max-width: 100%;
            border: 1px solid var(--dark-border);
            border-radius: 0.375rem;
            margin: 1rem 0;
        }
        
        /* Media Queries */
        @media (max-width: 640px) {
            .result-row {
                flex-direction: column;
                gap: 0.25rem;
            }
            
            .tab-container {
                overflow-x: auto;
                white-space: nowrap;
            }
        }
    </style>
</head>
<body class="min-h-screen">
    <!-- Notification Container -->
    <div id="notification" class="notification">
        <div class="mr-3">
            <i id="notification-icon" class="fas fa-info-circle"></i>
        </div>
        <div id="notification-message"></div>
    </div>

    <!-- Header -->
    <header class="site-header py-3 px-4 flex items-center justify-between">
        <div class="flex items-center">
            <button id="menu-toggle" class="mr-3 text-2xl">
                <i class="fas fa-bars"></i>
            </button>
            <a href="https://vtzspaxe.com/" target="_blank" class="flex items-center">
                <img src="https://raw.githubusercontent.com/vtzai2024/TinhMatDoXayDung/main/LOGO%20VUONG%20NEN%20TRONG%20SUOT%20-chu%20trang-small.png" 
                     alt="VTZ Spaxe" class="h-10 w-10 mr-2">
                <div>
                    <div class="font-bold text-lg">VTZ Spaxe</div>
                    <div class="text-xs text-gray-400">Thiết kế & Xây dựng</div>
                </div>
            </a>
        </div>
        <h1 class="text-lg font-bold">Tư vấn xây dựng theo QĐ 56-2021</h1>
    </header>

    <!-- Navigation -->
    <div id="nav-overlay" class="nav-overlay fixed top-0 left-0 w-full h-full z-50 hidden">
        <div class="bg-gray-900 w-64 h-full p-4 overflow-y-auto">
            <div class="flex items-center justify-between mb-6">
                <a href="https://vtzspaxe.com/" target="_blank" class="flex items-center">
                    <img src="https://raw.githubusercontent.com/vtzai2024/TinhMatDoXayDung/main/LOGO%20VUONG%20NEN%20TRONG%20SUOT%20-chu%20trang-small.png" 
                         alt="VTZ Spaxe" class="h-10 w-10 mr-2">
                    <div class="font-bold text-xl">VTZ Spaxe</div>
                </a>
                <button id="close-menu" class="text-white text-2xl">
                    <i class="fas fa-times"></i>
                </button>
            </div>
            <nav>
                <div class="mb-2 text-xs text-gray-500 uppercase">Thông tin chính</div>
                <a href="#nhap-du-lieu" class="nav-item px-4 py-3 flex items-center mb-1 rounded active">
                    <i class="fas fa-edit mr-3"></i>
                    <span>Nhập dữ liệu</span>
                </a>
                <a href="#ket-qua" class="nav-item px-4 py-3 flex items-center mb-1 rounded">
                    <i class="fas fa-calculator mr-3"></i>
                    <span>Kết quả tính toán</span>
                </a>
                <a href="#khai-toan" class="nav-item px-4 py-3 flex items-center mb-1 rounded">
                    <i class="fas fa-file-invoice-dollar mr-3"></i>
                    <span>Khái toán chi phí</span>
                </a>
                <a href="#lo-dat-dac-biet" class="nav-item px-4 py-3 flex items-center mb-1 rounded">
                    <i class="fas fa-map-marker-alt mr-3"></i>
                    <span>Lô đất đặc biệt</span>
                </a>
                <a href="#huong-dan" class="nav-item px-4 py-3 flex items-center mb-1 rounded">
                    <i class="fas fa-book mr-3"></i>
                    <span>Hướng dẫn sử dụng</span>
                </a>
                <div class="mb-2 mt-4 text-xs text-gray-500 uppercase">Thông tin thêm</div>
                <a href="#lien-he" class="nav-item px-4 py-3 flex items-center mb-1 rounded">
                    <i class="fas fa-phone mr-3"></i>
                    <span>Liên hệ tư vấn</span>
                </a>
                <a href="#gioi-thieu" class="nav-item px-4 py-3 flex items-center mb-1 rounded">
                    <i class="fas fa-building mr-3"></i>
                    <span>Giới thiệu công ty</span>
                </a>
            </nav>
        </div>
    </div>

    <!-- Main Content Container -->
    <main class="container mx-auto px-4 py-6 pb-24">
        <!-- Tab Navigation -->
        <div class="tab-container flex mb-6 border-b border-gray-700 overflow-x-auto whitespace-nowrap">
            <button class="tab-button px-4 py-2 font-medium text-sm active" data-tab="nhap-du-lieu">
                <i class="fas fa-edit mr-2"></i>Nhập dữ liệu
            </button>
            <button class="tab-button px-4 py-2 font-medium text-sm" data-tab="ket-qua">
                <i class="fas fa-calculator mr-2"></i>Kết quả
            </button>
            <button class="tab-button px-4 py-2 font-medium text-sm" data-tab="khai-toan">
                <i class="fas fa-file-invoice-dollar mr-2"></i>Khái toán
            </button>
            <button class="tab-button px-4 py-2 font-medium text-sm" data-tab="lo-dat-dac-biet">
                <i class="fas fa-map-marker-alt mr-2"></i>Lô đất đặc biệt
            </button>
            <button class="tab-button px-4 py-2 font-medium text-sm" data-tab="huong-dan">
                <i class="fas fa-book mr-2"></i>Hướng dẫn
            </button>
        </div>

        <!-- Tabs Content -->
        
        <!-- Nhập dữ liệu Tab -->
        <div id="nhap-du-lieu" class="tab-content active">
            <div class="grid grid-cols-1 gap-6">
                <!-- Thông tin lô đất -->
                <div class="card p-5">
                    <h2 class="text-xl font-bold mb-4 pb-2 card-header">
                        <i class="fas fa-info-circle mr-2"></i>Thông tin lô đất
                    </h2>
                    <div class="mt-4">
                        <div class="mb-4">
                            <label for="dienTichDat" class="form-label block mb-1">Diện tích lô đất (m²):</label>
                            <input type="number" id="dienTichDat" class="form-input w-full px-3 py-2 rounded" 
                                   placeholder="Nhập diện tích lô đất" min="0" step="0.01">
                            <div class="input-hint text-sm mt-1">Diện tích lô đất ảnh hưởng đến mật độ xây dựng tối đa</div>
                            <div id="dienTichDat-error" class="text-red-500 text-sm mt-1 hidden"></div>
                        </div>
                        <div class="mb-4">
                            <label for="chieuSauDat" class="form-label block mb-1">Chiều sâu lô đất (m):</label>
                            <input type="number" id="chieuSauDat" class="form-input w-full px-3 py-2 rounded" 
                                   placeholder="Nhập chiều sâu lô đất" min="0" step="0.01">
                            <div class="input-hint text-sm mt-1">Chiều sâu lô đất ảnh hưởng đến yêu cầu khoảng lùi</div>
                            <div id="chieuSauDat-error" class="text-red-500 text-sm mt-1 hidden"></div>
                        </div>
                        <div class="mb-4">
                            <label for="chieuRongLoGioi" class="form-label block mb-1">Chiều rộng lộ giới (m):</label>
                            <input type="number" id="chieuRongLoGioi" class="form-input w-full px-3 py-2 rounded" 
                                   placeholder="Nhập chiều rộng lộ giới" min="0" step="0.01">
                            <div class="input-hint text-sm mt-1">Chiều rộng lộ giới ảnh hưởng đến số tầng và chiều cao</div>
                            <div id="chieuRongLoGioi-error" class="text-red-500 text-sm mt-1 hidden"></div>
                        </div>
                        <div class="mb-4">
                            <label for="chieuRongMatTien" class="form-label block mb-1">Chiều rộng mặt tiền (m):</label>
                            <input type="number" id="chieuRongMatTien" class="form-input w-full px-3 py-2 rounded" 
                                   placeholder="Nhập chiều rộng mặt tiền" min="0" step="0.01">
                            <div class="input-hint text-sm mt-1">Chiều rộng mặt tiền ảnh hưởng đến số tầng cộng thêm</div>
                            <div id="chieuRongMatTien-error" class="text-red-500 text-sm mt-1 hidden"></div>
                        </div>
                        <div class="mt-5">
                            <p class="font-medium mb-3">Điều kiện đặc biệt:</p>
                            <div class="mb-2">
                                <label class="checkbox-label">
                                    <input type="checkbox" id="quanTrungTam" name="viTri" class="form-checkbox mr-2">
                                    <span>Thuộc Quận trung tâm hoặc Trung tâm cấp quận</span>
                                </label>
                            </div>
                            <div class="mb-2">
                                <label class="checkbox-label">
                                    <input type="checkbox" id="trucDuongThuongMai" name="viTri" class="form-checkbox mr-2">
                                    <span>Thuộc trục đường thương mại - dịch vụ</span>
                                </label>
                            </div>
                            <div class="mb-2">
                                <label class="checkbox-label">
                                    <input type="checkbox" id="matTienTren8m" name="viTri" class="form-checkbox mr-2">
                                    <span>Có chiều rộng mặt tiền > 8,0m</span>
                                </label>
                            </div>
                            <div class="mb-2">
                                <label class="checkbox-label">
                                    <input type="checkbox" id="loDatGoc" name="viTri" class="form-checkbox mr-2">
                                    <span>Lô đất góc (tiếp giáp 2+ đường)</span>
                                </label>
                            </div>
                        </div>
                    </div>
                </div>

                <!-- Đơn giá thi công -->
                <div class="card p-5">
                    <h2 class="text-xl font-bold mb-4 pb-2 card-header">
                        <i class="fas fa-dollar-sign mr-2"></i>Đơn giá thi công
                    </h2>
                    <div class="mt-4">
                        <div class="mb-4">
                            <label for="donGiaThietKe" class="form-label block mb-1">Đơn giá thiết kế (VNĐ/m²):</label>
                            <input type="text" id="donGiaThietKe" class="form-input w-full px-3 py-2 rounded currency-input" 
                                   value="250.000" placeholder="VNĐ/m²">
                        </div>
                        <div class="mb-4">
                            <label for="donGiaPhanTho" class="form-label block mb-1">Đơn giá phần thô (VNĐ/m²):</label>
                            <input type="text" id="donGiaPhanTho" class="form-input w-full px-3 py-2 rounded currency-input" 
                                   value="4.000.000" placeholder="VNĐ/m²">
                        </div>
                        <div class="mb-4">
                            <label for="donGiaHoanThien" class="form-label block mb-1">Đơn giá hoàn thiện (VNĐ/m²):</label>
                            <input type="text" id="donGiaHoanThien" class="form-input w-full px-3 py-2 rounded currency-input" 
                                   value="2.500.000" placeholder="VNĐ/m²">
                        </div>
                        <div class="mb-4">
                            <label for="donGiaNoiThat" class="form-label block mb-1">Đơn giá hoàn thiện nội thất (VNĐ/m²):</label>
                            <input type="text" id="donGiaNoiThat" class="form-input w-full px-3 py-2 rounded currency-input" 
                                   value="2.000.000" placeholder="VNĐ/m²">
                        </div>
                        <div class="mt-5">
                            <p class="font-medium mb-3">Tùy chọn bổ sung:</p>
                            <div class="mb-2">
                                <label class="checkbox-label">
                                    <input type="checkbox" id="coTangLung" name="tangLung" class="form-checkbox mr-2" checked>
                                    <span>Có tầng lửng</span>
                                </label>
                                <span id="tangLungInfo" class="ml-2 text-sm text-gray-400">Chỉ được phép khi chiều rộng lộ giới ≥ 6m</span>
                            </div>
                            <div class="mb-2">
                                <label class="checkbox-label">
                                    <input type="checkbox" id="coTangDinhMai" name="tangDinhMai" class="form-checkbox mr-2" checked disabled>
                                    <span>Có tầng đỉnh mái</span>
                                </label>
                                <span class="ml-2 px-2 py-0.5 bg-blue-900 text-blue-200 text-xs rounded">Bắt buộc</span>
                            </div>
                            <div class="mb-2">
                                <label class="checkbox-label">
                                    <input type="checkbox" id="coSanThuong" name="sanThuong" class="form-checkbox mr-2" checked>
                                    <span>Có sân thượng</span>
                                </label>
                            </div>
                            <div class="mb-2">
                                <label class="checkbox-label">
                                    <input type="checkbox" id="coMaiBTCT" name="maiBTCT" class="form-checkbox mr-2" checked>
                                    <span>Có mái BTCT</span>
                                </label>
                            </div>
                        </div>
                    </div>
                </div>

                <!-- Diện tích xây dựng -->
                <div class="card p-5">
                    <h2 class="text-xl font-bold mb-4 pb-2 card-header">
                        <i class="fas fa-ruler-combined mr-2"></i>Diện tích xây dựng
                    </h2>
                    <div class="mt-4">
                        <!-- Tầng hầm -->
                        <div class="mb-6 pb-4 border-b border-gray-700">
                            <h3 class="font-bold text-blue-400 mb-3">
                                <i class="fas fa-arrow-down mr-2"></i>Tầng hầm
                            </h3>
                            <div class="mb-2">
                                <label class="radio-label mr-4">
                                    <input type="radio" name="tangHam" value="none" checked class="form-radio mr-2">
                                    <span>Không có tầng hầm</span>
                                </label>
                                <label class="radio-label">
                                    <input type="radio" name="tangHam" value="ham" class="form-radio mr-2">
                                    <span>Có tầng hầm</span>
                                </label>
                            </div>
                            <div id="tangHamOptions" class="pl-4 mt-3 hidden">
                                <div class="grid grid-cols-1 sm:grid-cols-2 gap-3">
                                    <div>
                                        <label class="radio-label block mb-2">
                                            <input type="radio" name="doSauHam" id="doSau1" value="1.5" class="form-radio mr-2">
                                            <span class="flex justify-between w-full">
                                                <span>Sâu 1.0m - 1.3m</span>
                                                <span class="text-blue-400">150%</span>
                                            </span>
                                        </label>
                                    </div>
                                    <div>
                                        <label class="radio-label block mb-2">
                                            <input type="radio" name="doSauHam" id="doSau2" value="1.7" class="form-radio mr-2">
                                            <span class="flex justify-between w-full">
                                                <span>Sâu 1.3m - 1.7m</span>
                                                <span class="text-blue-400">170%</span>
                                            </span>
                                        </label>
                                    </div>
                                    <div>
                                        <label class="radio-label block mb-2">
                                            <input type="radio" name="doSauHam" id="doSau3" value="2.0" class="form-radio mr-2">
                                            <span class="flex justify-between w-full">
                                                <span>Sâu 1.7m - 2.0m</span>
                                                <span class="text-blue-400">200%</span>
                                            </span>
                                        </label>
                                    </div>
                                    <div>
                                        <label class="radio-label block mb-2">
                                            <input type="radio" name="doSauHam" id="doSau4" value="2.2" class="form-radio mr-2">
                                            <span class="flex justify-between w-full">
                                                <span>Sâu trên 2.0m</span>
                                                <span class="text-blue-400">220%</span>
                                            </span>
                                        </label>
                                    </div>
                                </div>
                                <div class="mt-2">
                                    <label class="checkbox-label">
                                        <input type="checkbox" id="hamNho" class="form-checkbox mr-2">
                                        <span>Hầm có diện tích sử dụng < 70m²</span>
                                    </label>
                                    <span class="ml-2 px-2 py-0.5 bg-blue-900 text-blue-200 text-xs rounded">+20%</span>
                                </div>
                            </div>
                        </div>
                        
                        <!-- Móng -->
                        <div class="mb-6 pb-4 border-b border-gray-700">
                            <h3 class="font-bold text-blue-400 mb-3">
                                <i class="fas fa-arrow-down mr-2"></i>Móng
                            </h3>
                            <div class="grid grid-cols-1 sm:grid-cols-2 gap-3">
                                <div>
                                    <label class="radio-label block mb-2">
                                        <input type="radio" name="loaiMong" id="mongDon" value="0.3" checked class="form-radio mr-2">
                                        <span class="flex justify-between w-full">
                                            <span>Móng đơn</span>
                                            <span class="text-blue-400">30%</span>
                                        </span>
                                    </label>
                                </div>
                                <div>
                                    <label class="radio-label block mb-2">
                                        <input type="radio" name="loaiMong" id="mongCoc" value="0.5" class="form-radio mr-2">
                                        <span class="flex justify-between w-full">
                                            <span>Móng cọc</span>
                                            <span class="text-blue-400">50%</span>
                                        </span>
                                    </label>
                                </div>
                                <div>
                                    <label class="radio-label block mb-2">
                                        <input type="radio" name="loaiMong" id="mongBang" value="0.5" class="form-radio mr-2">
                                        <span class="flex justify-between w-full">
                                            <span>Móng băng</span>
                                            <span class="text-blue-400">50%</span>
                                        </span>
                                    </label>
                                </div>
                                <div>
                                    <label class="radio-label block mb-2">
                                        <input type="radio" name="loaiMong" id="mongBe" value="0.8" class="form-radio mr-2">
                                        <span class="flex justify-between w-full">
                                            <span>Móng bè</span>
                                            <span class="text-blue-400">80%</span>
                                        </span>
                                    </label>
                                </div>
                            </div>
                        </div>
                        
                        <!-- Mái -->
                        <div class="mb-4">
                            <h3 class="font-bold text-blue-400 mb-3">
                                <i class="fas fa-home mr-2"></i>Mái
                            </h3>
                            <div class="grid grid-cols-1 sm:grid-cols-2 gap-3">
                                <div>
                                    <label class="radio-label block mb-2">
                                        <input type="radio" name="loaiMai" id="maiBTCT" value="0.5" checked class="form-radio mr-2">
                                        <span class="flex justify-between w-full">
                                            <span>Mái bê tông cốt thép</span>
                                            <span class="text-blue-400">50%</span>
                                        </span>
                                    </label>
                                </div>
                                <div>
                                    <label class="radio-label block mb-2">
                                        <input type="radio" name="loaiMai" id="maiTon" value="0.3" class="form-radio mr-2">
                                        <span class="flex justify-between w-full">
                                            <span>Mái tôn</span>
                                            <span class="text-blue-400">30%</span>
                                        </span>
                                    </label>
                                </div>
                                <div>
                                    <label class="radio-label block mb-2">
                                        <input type="radio" name="loaiMai" id="maiNgoi" value="0.7" class="form-radio mr-2">
                                        <span class="flex justify-between w-full">
                                            <span>Mái ngói kèo sắt</span>
                                            <span class="text-blue-400">70%</span>
                                        </span>
                                    </label>
                                </div>
                                <div>
                                    <label class="radio-label block mb-2">
                                        <input type="radio" name="loaiMai" id="maiXienBTCT" value="0.8" class="form-radio mr-2">
                                        <span class="flex justify-between w-full">
                                            <span>Mái xiên BTCT</span>
                                            <span class="text-blue-400">80%</span>
                                        </span>
                                    </label>
                                </div>
                            </div>
                        </div>
                    </div>

                    <div class="mt-6">
                        <button id="tinhToanBtn" class="btn-primary w-full py-3 px-6 rounded-lg text-center flex items-center justify-center">
                            <i class="fas fa-calculator mr-2"></i>
                            <span>Tính toán</span>
                        </button>
                    </div>
                </div>
            </div>
        </div>

        <!-- Kết quả tính toán Tab -->
        <div id="ket-qua" class="tab-content">
            <div class="card p-5">
                <h2 class="text-xl font-bold mb-4 pb-2 card-header">
                    <i class="fas fa-calculator mr-2"></i>Kết quả tính toán
                </h2>

                <div id="no-calculations" class="text-center py-10">
                    <i class="fas fa-calculator text-4xl mb-4 text-gray-500"></i>
                    <p>Vui lòng nhập dữ liệu và nhấn "Tính toán" để xem kết quả.</p>
                </div>

                <div id="has-calculations" class="hidden">
                    <div id="loDatNhoWarning" class="alert alert-warning mb-4 hidden">
                        <div class="flex">
                            <div class="flex-shrink-0">
                                <i class="fas fa-exclamation-triangle text-yellow-500"></i>
                            </div>
                            <div class="ml-3">
                                <h3 class="text-sm font-medium text-yellow-400">Lô đất diện tích nhỏ</h3>
                                <div class="mt-2 text-sm" id="loDatNhoMessage">
                                </div>
                            </div>
                        </div>
                    </div>

                    <div class="grid grid-cols-1 md:grid-cols-2 gap-6">
                        <!-- Thông số cơ bản -->
                        <div class="result-section">
                            <div class="result-title font-semibold py-2 mb-3">
                                <i class="fas fa-info-circle mr-2"></i>Thông số cơ bản
                            </div>
                            <div class="result-row">
                                <span class="result-label">Diện tích lô đất:</span>
                                <span class="result-value" id="dienTichLoDat">--</span>
                            </div>
                            <div class="result-row">
                                <span class="result-label">Mật độ xây dựng:</span>
                                <span class="result-value" id="matDoXayDung">--</span>
                            </div>
                            <div class="result-row">
                                <span class="result-label">Diện tích được xây dựng:</span>
                                <span class="result-value" id="dienTichXayDung">--</span>
                            </div>
                            <div class="result-row">
                                <span class="result-label">Chiều rộng lộ giới:</span>
                                <span class="result-value" id="chieuRongLoGioiKQ">--</span>
                            </div>
                            <div class="result-row">
                                <span class="result-label">Chiều rộng mặt tiền:</span>
                                <span class="result-value" id="chieuRongMatTienKQ">--</span>
                            </div>
                        </div>

                        <!-- Khoảng lùi -->
                        <div class="result-section">
                            <div class="result-title font-semibold py-2 mb-3">
                                <i class="fas fa-arrows-alt-h mr-2"></i>Khoảng lùi
                            </div>
                            <div class="result-row">
                                <span class="result-label">Khoảng lùi phía sau:</span>
                                <span class="result-value" id="khoangLuiSau">--</span>
                            </div>
                            <div class="result-row">
                                <span class="result-label">Diện tích sân sau:</span>
                                <span class="result-value" id="dienTichSanSau">--</span>
                            </div>
                        </div>

                        <!-- Chiều cao và số tầng -->
                        <div class="result-section">
                            <div class="result-title font-semibold py-2 mb-3">
                                <i class="fas fa-building mr-2"></i>Chiều cao và số tầng
                            </div>
                            <div class="result-row">
                                <span class="result-label">Số tầng tối đa:</span>
                                <span class="result-value" id="soTangToiDa">--</span>
                            </div>
                            <div class="result-row">
                                <span class="result-label">Chiều cao tại CGXD:</span>
                                <span class="result-value" id="chieuCaoToiDaTaiCGXD">--</span>
                            </div>
                            <div class="result-row">
                                <span class="result-label">Chiều cao tại đỉnh mái:</span>
                                <span class="result-value" id="chieuCaoToiDaTaiDinhMai">--</span>
                            </div>
                            <div class="result-row">
                                <span class="result-label">Tầng lửng:</span>
                                <span class="result-value" id="thongTinTangLung">--</span>
                            </div>
                        </div>

                        <!-- Ban công và ô văng -->
                        <div class="result-section">
                            <div class="result-title font-semibold py-2 mb-3">
                                <i class="fas fa-home mr-2"></i>Ban công và ô văng
                            </div>
                            <div class="result-row">
                                <span class="result-label">Độ vươn tối đa của ban công:</span>
                                <span class="result-value" id="doVuonBanCong">--</span>
                            </div>
                            <div class="result-row">
                                <span class="result-label">Diện tích ban công:</span>
                                <span class="result-value" id="dienTichBanCong">--</span>
                            </div>
                        </div>
                    </div>

                    <div class="alert alert-info mt-6">
                        <div class="flex">
                            <div class="flex-shrink-0">
                                <i class="fas fa-info-circle text-blue-400"></i>
                            </div>
                            <div class="ml-3">
                                <h3 class="text-sm font-medium text-blue-400">Lưu ý quan trọng:</h3>
                                <div class="mt-2 text-sm">
                                    <p>Kết quả tính toán chỉ mang tính tham khảo theo quy định tại Phụ lục 18 - Quyết định số 56/2021/QĐ-UBND.</p>
                                    <p class="mt-1">Vui lòng liên hệ cơ quan có thẩm quyền để được hướng dẫn cụ thể khi thực hiện xây dựng.</p>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>

        <!-- Khái toán chi phí Tab -->
        <div id="khai-toan" class="tab-content">
            <div class="card p-5">
                <h2 class="text-xl font-bold mb-4 pb-2 card-header">
                    <i class="fas fa-file-invoice-dollar mr-2"></i>Khái toán chi phí xây dựng
                </h2>

                <div id="no-khai-toan" class="text-center py-10">
                    <i class="fas fa-file-invoice-dollar text-4xl mb-4 text-gray-500"></i>
                    <p>Vui lòng nhập dữ liệu và nhấn "Tính toán" để xem khái toán chi phí.</p>
                </div>

                <div id="has-khai-toan" class="hidden">
                    <div class="overflow-x-auto">
                        <table class="data-table" id="khaiToanTable">
                            <thead>
                                <tr>
                                    <th>STT</th>
                                    <th>Hạng mục</th>
                                    <th>DT (m²)</th>
                                    <th>Hệ số</th>
                                    <th>XD (m²)</th>
                                    <th>Xây</th>
                                </tr>
                            </thead>
                            <tbody id="khaiToanBody">
                                <!-- Dữ liệu sẽ được thêm bằng JavaScript -->
                            </tbody>
                        </table>
                    </div>

                    <div class="grid grid-cols-1 md:grid-cols-2 gap-6 mt-6 bg-gray-800 bg-opacity-50 p-4 rounded-lg">
                        <div>
                            <div class="flex justify-between items-center mb-3">
                                <span class="font-medium">Chi phí thiết kế:</span>
                                <span id="chiPhiThietKe" class="font-semibold text-blue-400">--</span>
                            </div>
                            <div class="flex justify-between items-center mb-3">
                                <span class="font-medium">Chi phí phần thô:</span>
                                <span id="chiPhiPhanTho" class="font-semibold text-blue-400">--</span>
                            </div>
                        </div>
                        <div>
                            <div class="flex justify-between items-center mb-3">
                                <span class="font-medium">Chi phí hoàn thiện:</span>
                                <span id="chiPhiHoanThien" class="font-semibold text-blue-400">--</span>
                            </div>
                            <div class="flex justify-between items-center mb-3">
                                <span class="font-medium">Chi phí nội thất:</span>
                                <span id="chiPhiNoiThat" class="font-semibold text-blue-400">--</span>
                            </div>
                        </div>
                    </div>

                    <div class="flex justify-between items-center mt-4 p-3 bg-blue-600 rounded-lg text-white">
                        <span class="font-bold text-lg">Tổng chi phí:</span>
                        <span id="tongChiPhi" class="font-bold text-lg">--</span>
                    </div>

                    <div class="mt-4 text-sm text-gray-400">
                        <h3 class="font-medium mb-2">Ghi chú:</h3>
                        <ul class="list-disc pl-5 space-y-1">
                            <li>Chi phí thiết kế = Tổng diện tích thiết kế × Đơn giá thiết kế</li>
                            <li>Chi phí phần thô = Tổng diện tích xây dựng × Đơn giá phần thô</li>
                            <li>Chi phí hoàn thiện = Tổng diện tích xây dựng × Đơn giá hoàn thiện</li>
                            <li>Chi phí nội thất = Tổng diện tích xây dựng × 0,85 × Đơn giá nội thất</li>
                            <li>Chi phí trên chưa bao gồm thuế VAT và các chi phí phát sinh khác</li>
                            <li><span class="font-medium text-blue-400">Lưu ý:</span> Tổng diện tích thiết kế không bao gồm diện tích móng nhà</li>
                        </ul>
                    </div>
                </div>
            </div>
        </div>

        <!-- Lô đất đặc biệt Tab -->
        <div id="lo-dat-dac-biet" class="tab-content">
            <div class="card p-5">
                <h2 class="text-xl font-bold mb-4 pb-2 card-header">
                    <i class="fas fa-map-marker-alt mr-2"></i>Lô đất có vị trí đặc biệt
                </h2>

                <p class="mb-4">Lô đất có vị trí đặc biệt là lô đất có vị trí tại góc giao của hai hoặc ba đường (hoặc hẻm) hoặc tiếp giáp hai đường (hoặc hẻm) có quy định khác nhau về tầng cao.</p>

                <h3 class="font-bold text-blue-400 mb-3 mt-6">Trường hợp lô đất góc giao hai hoặc ba đường</h3>
                
                <div class="mb-5 text-gray-300">
                    <p class="mb-3"><strong>a) Nếu chiều rộng lô đất nhỏ hơn 3,0m quay về phía đường lớn:</strong></p>
                    <p class="pl-4 mb-2">• Các chỉ tiêu quy hoạch kiến trúc được xác định theo quy định đối với đường nhỏ</p>
                    
                    <p class="mb-3 mt-4"><strong>b) Nếu chiều rộng lô đất tối thiểu 3,0m quay về phía đường lớn:</strong></p>
                    <p class="pl-4 mb-2">• Phần diện tích trong phạm vi 20m tính từ giao lộ: áp dụng quy định của đường lớn</p>
                    <p class="pl-4 mb-2">• Phần diện tích còn lại: áp dụng quy định của đường nhỏ</p>
                </div>

                <div class="bg-gray-800 rounded-lg p-4 mb-6">
                    <h4 class="font-bold text-blue-400 mb-3">Minh họa lô đất góc</h4>
                    <div class="text-center">
                        <p class="text-sm text-gray-400 mb-2">Hình ảnh minh họa lô đất góc với phạm vi áp dụng quy định của đường lớn trong vòng 20m</p>
                        <div class="h-36 bg-gray-700 rounded flex items-center justify-center mb-2">
                            <i class="fas fa-image text-4xl text-gray-500"></i>
                            <span class="ml-2 text-gray-500">Hình ảnh minh họa</span>
                        </div>
                    </div>
                </div>

                <h3 class="font-bold text-blue-400 mb-3 mt-6">Các trường hợp lô đất dưới 36m²</h3>
                
                <div class="mb-4">
                    <p class="mb-3"><strong>1. Điều kiện cơ bản:</strong></p>
                    <p class="pl-4 mb-2">• Lô đất phải có quy mô diện tích tối thiểu 36m²</p>
                    <p class="pl-4 mb-2">• Chiều rộng mặt tiền tại vị trí tiếp giáp lộ giới không nhỏ hơn 3,0m</p>
                    <p class="pl-4 mb-2">• Chiều sâu so với chỉ giới xây dựng không nhỏ hơn 3,0m</p>
                </div>
                
                <div class="alert alert-warning mb-4">
                    <div class="flex">
                        <div class="flex-shrink-0">
                            <i class="fas fa-exclamation-triangle text-yellow-500"></i>
                        </div>
                        <div class="ml-3">
                            <h3 class="text-sm font-medium text-yellow-400">Lô đất không đảm bảo điều kiện cơ bản</h3>
                            <div class="mt-2 text-sm">
                                <p class="mb-2"><strong>a) Chiều rộng mặt tiền hoặc chiều sâu < 3,0m:</strong></p>
                                <p class="pl-4 mb-2">• Chỉ được cải tạo, sửa chữa theo hiện trạng hoặc xây mới với chiều cao tối đa tại CGXD: 7,0m</p>
                                <p class="pl-4">• Chiều cao tại đỉnh mái không quá 9,0m</p>

                                <p class="mb-2 mt-3"><strong>b) Diện tích < 15m² (chiều rộng và chiều sâu ≥ 3,0m):</strong></p>
                                <p class="pl-4">• Chỉ được cải tạo, sửa chữa theo hiện trạng hoặc xây mới với chiều cao tối đa tại đỉnh mái: 7,0m</p>

                                <p class="mb-2 mt-3"><strong>c) Diện tích 15m² đến < 36m² (chiều rộng và chiều sâu ≥ 3,0m):</strong></p>
                                <p class="pl-4 mb-2">• Lộ giới ≥ 6m: Chiều cao tối đa tại CGXD: 11,6m, tại đỉnh mái: 13,6m</p>
                                <p class="pl-4">• Lộ giới < 6m: Chiều cao tối đa tại đỉnh mái: 11,6m</p>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>

        <!-- Hướng dẫn sử dụng Tab -->
        <div id="huong-dan" class="tab-content">
            <div class="card p-5">
                <h2 class="text-xl font-bold mb-4 pb-2 card-header">
                    <i class="fas fa-book mr-2"></i>Hướng dẫn sử dụng
                </h2>

                <div class="space-y-6 mt-4">
                    <div>
                        <h3 class="font-bold text-lg mb-3">Cách sử dụng ứng dụng</h3>
                        <ol class="list-decimal pl-5 space-y-2">
                            <li><strong>Nhập dữ liệu:</strong> Điền thông tin về lô đất trong tab "Nhập dữ liệu"</li>
                            <li><strong>Tính toán:</strong> Nhấn nút "Tính toán" để xem kết quả</li>
                            <li><strong>Xem kết quả:</strong> Chuyển đến tab "Kết quả" để xem thông tin chi tiết</li>
                            <li><strong>Khái toán chi phí:</strong> Xem dự toán chi phí xây dựng trong tab "Khái toán"</li>
                            <li><strong>Tham khảo thêm:</strong> Xem thông tin về các trường hợp đặc biệt trong tab "Lô đất đặc biệt"</li>
                        </ol>
                    </div>

                    <div>
                        <h3 class="font-bold text-lg mb-3">Mật độ xây dựng</h3>
                        <p class="mb-2">Được tính dựa trên diện tích lô đất theo Bảng 1 của Phụ lục 18:</p>
                        <div class="overflow-x-auto">
                            <table class="data-table">
                                <tr>
                                    <th>Diện tích lô đất (m²)</th>
                                    <th>Mật độ xây dựng tối đa (%)</th>
                                </tr>
                                <tr><td>≤ 50</td><td>100</td></tr>
                                <tr><td>100</td><td>90</td></tr>
                                <tr><td>200</td><td>70</td></tr>
                                <tr><td>300</td><td>60</td></tr>
                                <tr><td>500</td><td>50</td></tr>
                                <tr><td>> 500</td><td>50</td></tr>
                            </table>
                        </div>
                        <p class="mt-2 text-sm italic text-gray-400">Chú thích: Với diện tích đất nằm giữa các giá trị trong bảng, mật độ xây dựng được tính theo phương pháp nội suy.</p>
                    </div>

                    <div>
                        <h3 class="font-bold text-lg mb-3">Khoảng lùi phía sau</h3>
                        <p class="mb-2">Được tính dựa trên chiều sâu lô đất (D) theo mục 6 của Phụ lục 18:</p>
                        <ul class="list-disc pl-5 space-y-1">
                            <li>D ≥ 16m: Khoảng lùi tối thiểu 2m</li>
                            <li>9m ≤ D < 16m: Khoảng lùi tối thiểu 1m</li>
                            <li>D < 9m: Khuyến khích tạo khoảng trống phía sau nhà</li>
                        </ul>
                    </div>
                    
                    <div>
                        <h3 class="font-bold text-lg mb-3">Số tầng cao độ</h3>
                        <p class="mb-2">Dựa trên chiều rộng lộ giới (L) và các điều kiện đặc biệt:</p>
                        <ul class="list-disc pl-5 space-y-1">
                            <li>L ≥ 25m: 6 tầng</li>
                            <li>16m ≤ L < 25m: 5 tầng + tầng cộng thêm (nếu có điều kiện)</li>
                            <li>6m ≤ L < 16m: 4 tầng + tầng cộng thêm (nếu có điều kiện)</li>
                            <li>3.5m ≤ L < 6m: 3 tầng + tầng cộng thêm (nếu có điều kiện)</li>
                            <li>L < 3.5m: 3 tầng (không cộng thêm)</li>
                        </ul>
                        <p class="mt-2 text-sm italic text-gray-400">Điều kiện cộng thêm tầng: Thuộc Quận trung tâm/Trung tâm cấp quận, thuộc trục đường thương mại - dịch vụ, hoặc có chiều rộng mặt tiền > 8.0m.</p>
                    </div>

                    <div>
                        <h3 class="font-bold text-lg mb-3">Ban công và ô văng</h3>
                        <p class="mb-2">Độ vươn của ban công, ô văng nhô ra trên không gian lộ giới phụ thuộc vào chiều rộng lộ giới:</p>
                        <div class="overflow-x-auto">
                            <table class="data-table">
                                <tr>
                                    <th>Chiều rộng lộ giới L (m)</th>
                                    <th>Độ vươn tối đa (m)</th>
                                </tr>
                                <tr><td>L < 7</td><td>0</td></tr>
                                <tr><td>7 ≤ L < 12</td><td>0,9</td></tr>
                                <tr><td>12 ≤ L < 20</td><td>1,2</td></tr>
                                <tr><td>L ≥ 20</td><td>1,4</td></tr>
                            </table>
                        </div>
                        <p class="mt-2 text-sm italic text-gray-400">Lưu ý: Độ vươn phải nhỏ hơn chiều rộng vỉa hè ít nhất 1,0m. Mặt dưới của ban công, ô văng phải cao hơn mặt vỉa hè hiện hữu ổn định tối thiểu 3,5m.</p>
                    </div>
                </div>
            </div>
        </div>

    </main>

    <!-- Footer -->
    <footer class="fixed bottom-0 left-0 w-full bg-gray-900 text-gray-400 text-sm py-3 px-4 text-center z-10">
        <p>© 2023-2025 Công ty TNHH Thiết kế và xây dựng VTZ Spaxe. Đã đăng ký bản quyền.</p>
        <p class="mt-1">Ứng dụng được phát minh bởi công ty TNHH Thiết kế và xây dựng VTZ Spaxe</p>
    </footer>

    <script>
        // DOM Element References
        const menuToggle = document.getElementById('menu-toggle');
        const closeMenu = document.getElementById('close-menu');
        const navOverlay = document.getElementById('nav-overlay');
        const navItems = document.querySelectorAll('.nav-item');
        const tabButtons = document.querySelectorAll('.tab-button');
        const tabContents = document.querySelectorAll('.tab-content');
        const tinhToanBtn = document.getElementById('tinhToanBtn');
        const coTangLung = document.getElementById('coTangLung');
        const tangLungInfo = document.getElementById('tangLungInfo');
        const tangHamRadios = document.querySelectorAll('input[name="tangHam"]');
        const tangHamOptions = document.getElementById('tangHamOptions');
        const notification = document.getElementById('notification');
        const notificationIcon = document.getElementById('notification-icon');
        const notificationMessage = document.getElementById('notification-message');

        // Navigation Menu Toggle
        menuToggle.addEventListener('click', () => {
            navOverlay.classList.remove('hidden');
        });

        closeMenu.addEventListener('click', () => {
            navOverlay.classList.add('hidden');
        });

        // Close menu when clicking on a nav item
        navItems.forEach(item => {
            item.addEventListener('click', () => {
                navOverlay.classList.add('hidden');

                // Highlight active nav item
                navItems.forEach(navItem => navItem.classList.remove('active'));
                item.classList.add('active');

                // Get target tab
                const target = item.getAttribute('href').substring(1);
                
                // Switch to corresponding tab
                switchToTab(target);
            });
        });

        // Tab functionality
        tabButtons.forEach(button => {
            button.addEventListener('click', () => {
                const target = button.dataset.tab;
                switchToTab(target);
            });
        });

        function switchToTab(tabId) {
            // Deactivate all tabs
            tabButtons.forEach(btn => btn.classList.remove('active'));
            tabContents.forEach(content => content.classList.remove('active'));
            
            // Activate target tab
            const targetButton = document.querySelector(`.tab-button[data-tab="${tabId}"]`);
            const targetContent = document.getElementById(tabId);
            
            if (targetButton) targetButton.classList.add('active');
            if (targetContent) targetContent.classList.add('active');
        }

        // Update tầng lửng availability based on lộ giới
        document.getElementById('chieuRongLoGioi').addEventListener('input', function() {
            updateTangLungAvailability(parseFloat(this.value) || 0);
        });

        function updateTangLungAvailability(chieuRongLoGioi) {
            if (chieuRongLoGioi < 6) {
                coTangLung.checked = false;
                coTangLung.disabled = true;
                tangLungInfo.classList.add('text-red-500');
                tangLungInfo.classList.remove('text-gray-400');
            } else {
                coTangLung.disabled = false;
                tangLungInfo.classList.remove('text-red-500');
                tangLungInfo.classList.add('text-gray-400');
            }
        }

        // Update tầng hầm options
        tangHamRadios.forEach(radio => {
            radio.addEventListener('change', function() {
                if (this.value === 'ham') {
                    tangHamOptions.classList.remove('hidden');
                    // Set default value if none selected
                    if (!document.querySelector('input[name="doSauHam"]:checked')) {
                        document.getElementById('doSau1').checked = true;
                    }
                } else {
                    tangHamOptions.classList.add('hidden');
                }
            });
        });

        // Auto-check mặt tiền > 8m checkbox based on input
        document.getElementById('chieuRongMatTien').addEventListener('input', function() {
            const value = parseFloat(this.value) || 0;
            document.getElementById('matTienTren8m').checked = value > 8;
        });

        // Format currency inputs
        document.querySelectorAll('.currency-input').forEach(input => {
            input.addEventListener('blur', function() {
                const rawValue = this.value.replace(/\./g, '');
                if (rawValue && !isNaN(parseFloat(rawValue))) {
                    this.value = formatNumber(parseFloat(rawValue));
                }
            });
            
            input.addEventListener('focus', function() {
                const rawValue = this.value.replace(/\./g, '');
                if (rawValue && !isNaN(parseFloat(rawValue))) {
                    this.value = rawValue;
                }
            });
        });

        // Format number with thousand separator
        function formatNumber(number) {
            return number.toString().replace(/\B(?=(\d{3})+(?!\d))/g, ".");
        }

        // Format currency
        function formatCurrency(number) {
            return formatNumber(Math.round(number)) + ' VNĐ';
        }

        // Parse formatted number back to number
        function parseFormattedNumber(formattedNumber) {
            if (typeof formattedNumber === 'string') {
                return parseInt(formattedNumber.replace(/\./g, ''));
            }
            return formattedNumber;
        }

        // Show notification
        function showNotification(message, type) {
            notification.className = 'notification';
            notification.classList.add(type);
            
            if (type === 'success') {
                notificationIcon.className = 'fas fa-check-circle text-green-500';
            } else if (type === 'error') {
                notificationIcon.className = 'fas fa-exclamation-circle text-red-500';
            } else {
                notificationIcon.className = 'fas fa-info-circle text-blue-500';
            }
            
            notificationMessage.textContent = message;
            notification.classList.add('show');
            
            setTimeout(() => {
                notification.classList.remove('show');
            }, 3000);
        }

        // Show/hide error message
        function showError(fieldId, message) {
            const errorElement = document.getElementById(`${fieldId}-error`);
            if (errorElement) {
                errorElement.textContent = message;
                errorElement.classList.remove('hidden');
                document.getElementById(fieldId).classList.add('border-red-500');
            }
        }

        function hideError(fieldId) {
            const errorElement = document.getElementById(`${fieldId}-error`);
            if (errorElement) {
                errorElement.classList.add('hidden');
                document.getElementById(fieldId).classList.remove('border-red-500');
            }
        }

        // CALCULATION FUNCTIONS

        // Tính mật độ xây dựng
        function tinhMatDoXayDung(dienTichDat) {
            if (dienTichDat <= 50) {
                return 100;
            } else if (dienTichDat <= 100) {
                return Math.round(100 - (dienTichDat - 50) * (10 / 50));
            } else if (dienTichDat <= 200) {
                return Math.round(90 - (dienTichDat - 100) * (20 / 100));
            } else if (dienTichDat <= 300) {
                return Math.round(70 - (dienTichDat - 200) * (10 / 100));
            } else if (dienTichDat <= 500) {
                return Math.round(60 - (dienTichDat - 300) * (10 / 200));
            } else {
                return 50;
            }
        }

        // Tính khoảng lùi phía sau
        function tinhKhoangLuiSau(chieuSauDat) {
            if (chieuSauDat >= 16) {
                return 2; // 2 mét
            } else if (chieuSauDat >= 9) {
                return 1; // 1 mét
            } else {
                return 0.5; // Giả định 0.5m cho khoảng trống phía sau
            }
        }

        // Lấy khoảng lùi phía sau dạng text để hiển thị
        function getKhoangLuiSauText(chieuSauDat) {
            if (chieuSauDat >= 16) {
                return "Tối thiểu 2m";
            } else if (chieuSauDat >= 9) {
                return "Tối thiểu 1m";
            } else {
                return "Khuyến khích tạo khoảng trống phía sau";
            }
        }

        // Tính số tầng tối đa
        function tinhSoTangToiDa(chieuRongLoGioi, quanTrungTam, trucDuongThuongMai, matTienTren8m, dienTichDat, chieuRongMatTien, chieuSauDat) {
            let soTangCoBan = 0;
            let soTangCongThem = 0;

            // Kiểm tra điều kiện lô đất nhỏ
            if (dienTichDat < 36) {
                if (chieuRongMatTien < 3.0 || chieuSauDat < 3.0) {
                    // Trường hợp chiều rộng mặt tiền hoặc chiều sâu < 3,0m
                    return 2; // Tương đương với chiều cao tối đa 7.0m (thường là 2 tầng)
                } else if (dienTichDat < 15) {
                    // Trường hợp diện tích < 15m²
                    return 2; // Tương đương với chiều cao tối đa 7.0m (thường là 2 tầng)
                } else {
                    // Trường hợp diện tích 15m² đến < 36m²
                    if (chieuRongLoGioi >= 6) {
                        return 3; // Tương đương với chiều cao tối đa 11.6m (thường là 3 tầng)
                    } else {
                        return 3; // Tương đương với chiều cao tối đa 11.6m (thường là 3 tầng)
                    }
                }
            }

            // Xác định số tầng cơ bản theo chiều rộng lộ giới
            if (chieuRongLoGioi >= 25) {
                soTangCoBan = 6;
            } else if (chieuRongLoGioi >= 16) {
                soTangCoBan = 5;
                // Xét điều kiện cộng thêm
                if (quanTrungTam) soTangCongThem += 1;
                if (trucDuongThuongMai) soTangCongThem += 1;
                if (matTienTren8m) soTangCongThem += 1;
            } else if (chieuRongLoGioi >= 6) {
                soTangCoBan = 4;
                // Xét điều kiện cộng thêm
                if (quanTrungTam) soTangCongThem += 1;
                if (matTienTren8m) soTangCongThem += 1;
            } else if (chieuRongLoGioi >= 3.5) {
                soTangCoBan = 3;
                // Xét điều kiện cộng thêm
                if (quanTrungTam) soTangCongThem += 1;
                if (matTienTren8m) soTangCongThem += 1;
            } else {
                soTangCoBan = 3;
                // Không cộng thêm
            }

            // Giới hạn tối đa tầng
            let soTangToiDa = soTangCoBan;
            if (chieuRongLoGioi >= 16) {
                soTangToiDa = Math.min(soTangCoBan + soTangCongThem, 6);
            } else if (chieuRongLoGioi >= 6) {
                soTangToiDa = Math.min(soTangCoBan + soTangCongThem, 5);
            } else if (chieuRongLoGioi >= 3.5) {
                soTangToiDa = Math.min(soTangCoBan + soTangCongThem, 4);
            } else {
                soTangToiDa = 3; // Không cộng thêm
            }

            return soTangToiDa;
        }

        // Tính chiều cao tối đa
        function tinhChieuCaoToiDa(chieuRongLoGioi, soTang, dienTichDat, chieuRongMatTien, chieuSauDat) {
            let chieuCaoTaiCGXD = ""; // Chiều cao tại chỉ giới xây dựng
            let chieuCaoTaiDinhMai = ""; // Chiều cao tại đỉnh mái

            // Kiểm tra điều kiện lô đất nhỏ
            if (dienTichDat < 36) {
                if (chieuRongMatTien < 3.0 || chieuSauDat < 3.0) {
                    return {
                        taiCGXD: "7,0m",
                        taiDinhMai: "9,0m"
                    };
                } else if (dienTichDat < 15) {
                    return {
                        taiCGXD: "Không quy định riêng",
                        taiDinhMai: "7,0m"
                    };
                } else {
                    // Trường hợp diện tích 15m² đến < 36m²
                    if (chieuRongLoGioi >= 6) {
                        return {
                            taiCGXD: "11,6m",
                            taiDinhMai: "13,6m"
                        };
                    } else {
                        return {
                            taiCGXD: "Không quy định riêng",
                            taiDinhMai: "11,6m"
                        };
                    }
                }
            }

            // Xác định chiều cao theo Bảng 3
            if (chieuRongLoGioi >= 25) {
                chieuCaoTaiCGXD = "25,0m";
                chieuCaoTaiDinhMai = soTang > 6 ? "27,0m" : "25,0m";
            } else if (chieuRongLoGioi >= 16) {
                chieuCaoTaiCGXD = "21,6m";
                chieuCaoTaiDinhMai = soTang > 5 ? "27,0m" : "23,6m";
            } else if (chieuRongLoGioi >= 6) {
                chieuCaoTaiCGXD = "17,0m";
                chieuCaoTaiDinhMai = soTang > 4 ? "22,4m" : "19,0m";
            } else if (chieuRongLoGioi >= 3.5) {
                chieuCaoTaiCGXD = "11,6m";
                chieuCaoTaiDinhMai = soTang > 3 ? "15,6m" : "13,6m";
            } else {
                chieuCaoTaiCGXD = "Không quy định riêng";
                chieuCaoTaiDinhMai = "11,6m";
            }

            return {
                taiCGXD: chieuCaoTaiCGXD,
                taiDinhMai: chieuCaoTaiDinhMai
            };
        }

        // Xác định thông tin về tầng lửng
        function xacDinhTangLung(chieuRongLoGioi) {
            if (chieuRongLoGioi >= 6) {
                if (chieuRongLoGioi >= 16) {
                    return "Cho phép có tầng lửng, tổng chiều cao tầng 1 (bao gồm tầng lửng) tối đa 7,0m";
                } else {
                    return "Cho phép có tầng lửng, tổng chiều cao tầng 1 (bao gồm tầng lửng) tối đa 5,8m";
                }
            } else {
                return "Không được phép có tầng lửng (chiều rộng lộ giới < 6m)";
            }
        }

        // Tính độ vươn ban công
        function tinhDoVuonBanCong(chieuRongLoGioi) {
            let doVuon = 0;
            if (chieuRongLoGioi < 7) {
                doVuon = 0;
            } else if (chieuRongLoGioi < 12) {
                doVuon = 0.9;
            } else if (chieuRongLoGioi < 20) {
                doVuon = 1.2;
            } else {
                doVuon = 1.4;
            }
            return doVuon;
        }

        // Lấy độ vươn ban công dạng text để hiển thị
        function getDoVuonBanCongText(chieuRongLoGioi) {
            let doVuon = tinhDoVuonBanCong(chieuRongLoGioi);
            if (doVuon === 0) {
                return "0m (không được phép)";
            } else {
                return doVuon.toFixed(1) + "m";
            }
        }

        // Tính diện tích ban công
        function tinhDienTichBanCong(chieuRongLoGioi, chieuRongMatTien, soTang) {
            const doVuonBanCong = tinhDoVuonBanCong(chieuRongLoGioi);
            // Tính số tầng có ban công (từ tầng 1 trở lên)
            const soTangCoBanCong = soTang > 0 ? soTang - 1 : 0;
            return doVuonBanCong * chieuRongMatTien * soTangCoBanCong;
        }

        // Tính khái toán chi phí
        function tinhKhaiToanChiPhi(dienTichDat, soTang, matDoXayDung, chieuRongLoGioi, chieuRongMatTien, chieuSauDat) {
            // Lấy trạng thái checkbox từ giao diện
            const coTangLung = document.getElementById('coTangLung').checked && !document.getElementById('coTangLung').disabled;
            const coTangDinhMai = document.getElementById('coTangDinhMai').checked;
            const coSanThuong = document.getElementById('coSanThuong').checked;
            const coMaiBTCT = document.getElementById('coMaiBTCT').checked;
            
            // Lấy thông tin từ phần diện tích xây dựng
            const coTangHam = document.querySelector('input[name="tangHam"]:checked').value === 'ham';
            const doSauHam = coTangHam ? parseFloat(document.querySelector('input[name="doSauHam"]:checked')?.value || 0) : 0;
            const hamNho = coTangHam ? document.getElementById('hamNho').checked : false;
            const loaiMong = parseFloat(document.querySelector('input[name="loaiMong"]:checked').value || 0.3);
            const loaiMai = parseFloat(document.querySelector('input[name="loaiMai"]:checked').value || 0.5);

            // Diện tích XD tối đa theo mật độ xây dựng
            const dienTichXDMax = dienTichDat * matDoXayDung / 100;
            
            // Tính khoảng lùi sau và diện tích sân sau
            const khoangLuiSau = tinhKhoangLuiSau(chieuSauDat);
            const dienTichSanSau = khoangLuiSau * chieuRongMatTien;
            
            // Tính diện tích ban công
            const dienTichBanCong = tinhDienTichBanCong(chieuRongLoGioi, chieuRongMatTien, soTang);

            // Tạo bảng khái toán
            const khaiToanTable = [];
            let tongDienTichThietKe = 0;
            let tongDienTichXayDung = 0;
            let stt = 1;

            // Thêm móng nhà (dùng diện tích xây dựng tối đa làm diện tích cơ sở)
            khaiToanTable.push({
                stt: stt++,
                hangMuc: 'Móng nhà',
                dienTichDat: dienTichXDMax,
                heSo: loaiMong,
                dienTichXD: dienTichXDMax * loaiMong
            });
            // Không cộng vào tongDienTichThietKe như yêu cầu
            tongDienTichXayDung += dienTichXDMax * loaiMong;

            // Thêm tầng hầm nếu có
            if (coTangHam) {
                let heSoHam = doSauHam;
                if (hamNho) {
                    heSoHam += 0.2; // Cộng thêm 20% nếu hầm nhỏ
                }
                khaiToanTable.push({
                    stt: stt++,
                    hangMuc: 'Tầng hầm',
                    dienTichDat: dienTichXDMax,
                    heSo: heSoHam,
                    dienTichXD: dienTichXDMax * heSoHam
                });
                tongDienTichThietKe += dienTichXDMax;
                tongDienTichXayDung += dienTichXDMax * heSoHam;
            }

            // Thêm các tầng 1 đến số tầng tối đa
            for (let i = 1; i <= soTang; i++) {
                khaiToanTable.push({
                    stt: stt++,
                    hangMuc: `Tầng ${i}`,
                    dienTichDat: dienTichXDMax,
                    heSo: 1,
                    dienTichXD: dienTichXDMax
                });
                tongDienTichThietKe += dienTichXDMax;
                tongDienTichXayDung += dienTichXDMax;
            }

            // Thêm tầng lửng nếu được chọn và được phép
            if (coTangLung) {
                khaiToanTable.push({
                    stt: stt++,
                    hangMuc: 'Tầng lửng',
                    dienTichDat: dienTichXDMax,
                    heSo: 0.65,
                    dienTichXD: dienTichXDMax * 0.65
                });
                tongDienTichThietKe += dienTichXDMax * 0.65;
                tongDienTichXayDung += dienTichXDMax * 0.65;
            }

            // Tầng đỉnh mái (luôn được tính)
            if (coTangDinhMai) {
                khaiToanTable.push({
                    stt: stt++,
                    hangMuc: 'Tầng đỉnh mái',
                    dienTichDat: dienTichXDMax,
                    heSo: 0.35,
                    dienTichXD: dienTichXDMax * 0.35
                });
                tongDienTichThietKe += dienTichXDMax * 0.35;
                tongDienTichXayDung += dienTichXDMax * 0.35;
            }

            // Sân thượng
            if (coSanThuong) {
                khaiToanTable.push({
                    stt: stt++,
                    hangMuc: 'Sân thượng',
                    dienTichDat: dienTichXDMax,
                    heSo: 0.325,
                    dienTichXD: dienTichXDMax * 0.325
                });
                tongDienTichThietKe += dienTichXDMax * 0.325;
                tongDienTichXayDung += dienTichXDMax * 0.325;
            }

            // Ban công (nếu có)
            if (dienTichBanCong > 0) {
                khaiToanTable.push({
                    stt: stt++,
                    hangMuc: 'Ban công',
                    dienTichDat: dienTichBanCong,
                    heSo: 0.5,
                    dienTichXD: dienTichBanCong * 0.5
                });
                tongDienTichThietKe += dienTichBanCong * 0.5;
                tongDienTichXayDung += dienTichBanCong * 0.5;
            }

            // Sân sau
            if (dienTichSanSau > 0) {
                khaiToanTable.push({
                    stt: stt++,
                    hangMuc: 'Sân sau',
                    dienTichDat: dienTichSanSau,
                    heSo: 0.7,
                    dienTichXD: dienTichSanSau * 0.7
                });
                tongDienTichThietKe += dienTichSanSau * 0.7;
                tongDienTichXayDung += dienTichSanSau * 0.7;
            }

            return {
                khaiToanTable: khaiToanTable,
                tongDienTichThietKe: tongDienTichThietKe,
                tongDienTichXayDung: tongDienTichXayDung
            };
        }

        // Hiển thị bảng khái toán
        function renderKhaiToanTable(khaiToanTable) {
            const tableBody = document.getElementById('khaiToanBody');
            tableBody.innerHTML = '';

            // Thêm các hàng vào bảng
            khaiToanTable.forEach((item, index) => {
                const row = document.createElement('tr');
                
                // Lưu dữ liệu vào thuộc tính dataset của row
                row.dataset.dienTichDat = item.dienTichDat || 0;
                row.dataset.heSo = item.heSo || 0;
                row.dataset.dienTichXD = item.dienTichXD || 0;
                
                // Kiểm tra xem có phải là dòng tổng không
                const isTotalRow = index === khaiToanTable.length - 1;
                
                // Thêm class cho dòng tổng
                if (isTotalRow) {
                    row.classList.add('total-row');
                }
                
                // Tạo cột STT
                const sttCell = document.createElement('td');
                sttCell.textContent = item.stt;
                row.appendChild(sttCell);
                
                // Tạo cột Hạng mục
                const hangMucCell = document.createElement('td');
                hangMucCell.textContent = item.hangMuc;
                row.appendChild(hangMucCell);
                
                // Tạo cột Diện tích cơ sở
                const dienTichDatCell = document.createElement('td');
                dienTichDatCell.textContent = item.dienTichDat ? item.dienTichDat.toFixed(1) : '';
                row.appendChild(dienTichDatCell);
                
                // Tạo cột Hệ số
                const heSoCell = document.createElement('td');
                heSoCell.textContent = item.heSo ? item.heSo : '';
                row.appendChild(heSoCell);
                
                // Tạo cột Diện tích XD
                const dienTichXDCell = document.createElement('td');
                dienTichXDCell.textContent = item.dienTichXD ? item.dienTichXD.toFixed(1) : '';
                row.appendChild(dienTichXDCell);
                
                // Tạo cột Xây dựng (checkbox)
                const xayDungCell = document.createElement('td');
                // Nếu không phải dòng tổng thì thêm checkbox
                if (!isTotalRow) {
                    const checkbox = document.createElement('input');
                    checkbox.type = 'checkbox';
                    checkbox.checked = true;
                    checkbox.className = 'build-checkbox';
                    checkbox.addEventListener('change', updateCostBasedOnSelection);
                    
                    // Nếu là tầng đỉnh mái thì không cho bỏ chọn
                    if (item.hangMuc === 'Tầng đỉnh mái') {
                        checkbox.disabled = true;
                        checkbox.checked = true;
                        const label = document.createElement('span');
                        label.textContent = ' BT';
                        label.style.fontSize = '0.8em';
                        label.style.color = '#3B82F6';
                        xayDungCell.appendChild(checkbox);
                        xayDungCell.appendChild(label);
                    } else {
                        xayDungCell.appendChild(checkbox);
                    }
                }
                row.appendChild(xayDungCell);
                
                tableBody.appendChild(row);
            });

            // Gán sự kiện cho các checkbox
            document.querySelectorAll('.build-checkbox').forEach(checkbox => {
                checkbox.addEventListener('change', updateCostBasedOnSelection);
            });
        }

        // Xử lý sự kiện khi tick/untick tầng cần xây dựng
        function updateCostBasedOnSelection() {
            // Lấy tất cả các checkbox tầng cần xây dựng
            const buildCheckboxes = document.querySelectorAll('.build-checkbox');
            let tongDienTichThietKe = 0;
            let tongDienTichXayDung = 0;
            
            // Tính lại tổng diện tích dựa trên các hạng mục được chọn
            buildCheckboxes.forEach(checkbox => {
                if (checkbox.checked) {
                    const row = checkbox.closest('tr');
                    const dienTichXD = parseFloat(row.dataset.dienTichXD || 0);
                    const heSo = parseFloat(row.dataset.heSo || 0);
                    const dienTichDat = parseFloat(row.dataset.dienTichDat || 0);
                    
                    tongDienTichXayDung += dienTichXD;
                    
                    // Chỉ tính vào diện tích thiết kế nếu không phải móng nhà
                    const hangMuc = row.cells[1].textContent;
                    if (hangMuc !== 'Móng nhà' && heSo > 0 && dienTichDat > 0) {
                        tongDienTichThietKe += dienTichXD;
                    }
                }
            });
            
            // Cập nhật lại các chi phí
            const donGiaThietKe = parseFormattedNumber(document.getElementById('donGiaThietKe').value) || 250000;
            const donGiaPhanTho = parseFormattedNumber(document.getElementById('donGiaPhanTho').value) || 4000000;
            const donGiaHoanThien = parseFormattedNumber(document.getElementById('donGiaHoanThien').value) || 2500000;
            const donGiaNoiThat = parseFormattedNumber(document.getElementById('donGiaNoiThat').value) || 2000000;
            
            const chiPhiThietKe = tongDienTichThietKe * donGiaThietKe;
            const chiPhiPhanTho = tongDienTichXayDung * donGiaPhanTho;
            const chiPhiHoanThien = tongDienTichXayDung * donGiaHoanThien;
            const chiPhiNoiThat = tongDienTichXayDung * 0.85 * donGiaNoiThat;
            
            const tongChiPhi = chiPhiThietKe + chiPhiPhanTho + chiPhiHoanThien + chiPhiNoiThat;
            
            // Tính phần trăm của từng chi phí
            const percentThietKe = ((chiPhiThietKe / tongChiPhi) * 100).toFixed(1);
            const percentPhanTho = ((chiPhiPhanTho / tongChiPhi) * 100).toFixed(1);
            const percentHoanThien = ((chiPhiHoanThien / tongChiPhi) * 100).toFixed(1);
            const percentNoiThat = ((chiPhiNoiThat / tongChiPhi) * 100).toFixed(1);
            
            // Hiển thị lại các chi phí với phần trăm
            document.getElementById('chiPhiThietKe').innerHTML = `${formatCurrency(chiPhiThietKe)} <small class="text-gray-400">(${percentThietKe}%)</small>`;
            document.getElementById('chiPhiPhanTho').innerHTML = `${formatCurrency(chiPhiPhanTho)} <small class="text-gray-400">(${percentPhanTho}%)</small>`;
            document.getElementById('chiPhiHoanThien').innerHTML = `${formatCurrency(chiPhiHoanThien)} <small class="text-gray-400">(${percentHoanThien}%)</small>`;
            document.getElementById('chiPhiNoiThat').innerHTML = `${formatCurrency(chiPhiNoiThat)} <small class="text-gray-400">(${percentNoiThat}%)</small>`;
            document.getElementById('tongChiPhi').textContent = formatCurrency(tongChiPhi);
        }

        // Tính toán Button Click Handler
        tinhToanBtn.addEventListener('click', function() {
            // Kiểm tra dữ liệu đầu vào
            let isValid = true;
            const dienTichDat = parseFloat(document.getElementById('dienTichDat').value);
            const chieuSauDat = parseFloat(document.getElementById('chieuSauDat').value);
            const chieuRongLoGioi = parseFloat(document.getElementById('chieuRongLoGioi').value);
            const chieuRongMatTien = parseFloat(document.getElementById('chieuRongMatTien').value);
            
            // Kiểm tra và hiển thị thông báo lỗi nếu cần
            if (isNaN(dienTichDat) || dienTichDat <= 0) {
                showError('dienTichDat', 'Vui lòng nhập diện tích lô đất hợp lệ');
                isValid = false;
            } else {
                hideError('dienTichDat');
            }
            
            if (isNaN(chieuSauDat) || chieuSauDat <= 0) {
                showError('chieuSauDat', 'Vui lòng nhập chiều sâu lô đất hợp lệ');
                isValid = false;
            } else {
                hideError('chieuSauDat');
            }
            
            if (isNaN(chieuRongLoGioi) || chieuRongLoGioi <= 0) {
                showError('chieuRongLoGioi', 'Vui lòng nhập chiều rộng lộ giới hợp lệ');
                isValid = false;
            } else {
                hideError('chieuRongLoGioi');
            }
            
            if (isNaN(chieuRongMatTien) || chieuRongMatTien <= 0) {
                showError('chieuRongMatTien', 'Vui lòng nhập chiều rộng mặt tiền hợp lệ');
                isValid = false;
            } else {
                hideError('chieuRongMatTien');
            }
            
            if (!isValid) {
                showNotification('Vui lòng nhập đầy đủ thông tin lô đất', 'error');
                return;
            }
            
            // Lấy giá trị từ các checkbox
            const quanTrungTam = document.getElementById('quanTrungTam').checked;
            const trucDuongThuongMai = document.getElementById('trucDuongThuongMai').checked;
            const matTienTren8m = document.getElementById('matTienTren8m').checked || chieuRongMatTien > 8.0;
            const loDatGoc = document.getElementById('loDatGoc').checked;
            
            // Tính mật độ xây dựng
            const matDo = tinhMatDoXayDung(dienTichDat);
            
            // Tính diện tích được xây dựng
            const dienTichXD = (dienTichDat * matDo / 100).toFixed(1);
            
            // Tính khoảng lùi phía sau
            const khoangLuiSau = tinhKhoangLuiSau(chieuSauDat);
            const khoangLuiSauText = getKhoangLuiSauText(chieuSauDat);
            
            // Tính diện tích sân sau
            const dienTichSanSau = (khoangLuiSau * chieuRongMatTien).toFixed(1);
            
            // Tính số tầng tối đa
            const soTang = tinhSoTangToiDa(chieuRongLoGioi, quanTrungTam, trucDuongThuongMai, matTienTren8m, dienTichDat, chieuRongMatTien, chieuSauDat);
            
            // Tính chiều cao tối đa
            const chieuCao = tinhChieuCaoToiDa(chieuRongLoGioi, soTang, dienTichDat, chieuRongMatTien, chieuSauDat);
            
            // Xác định thông tin về tầng lửng
            const thongTinTangLung = xacDinhTangLung(chieuRongLoGioi);
            
            // Tính độ vươn của ban công
            const doVuonBanCongText = getDoVuonBanCongText(chieuRongLoGioi);
            
            // Tính diện tích ban công
            const dienTichBanCong = tinhDienTichBanCong(chieuRongLoGioi, chieuRongMatTien, soTang);
            
            // Tính khái toán chi phí
            const khaiToan = tinhKhaiToanChiPhi(dienTichDat, soTang, matDo, chieuRongLoGioi, chieuRongMatTien, chieuSauDat);
            
            // Hiển thị kết quả
            document.getElementById('no-calculations').classList.add('hidden');
            document.getElementById('has-calculations').classList.remove('hidden');
            
            document.getElementById('dienTichLoDat').textContent = dienTichDat + ' m²';
            document.getElementById('dienTichXayDung').textContent = dienTichXD + ' m²';
            document.getElementById('matDoXayDung').textContent = matDo + ' %';
            document.getElementById('chieuRongLoGioiKQ').textContent = chieuRongLoGioi + ' m';
            document.getElementById('chieuRongMatTienKQ').textContent = chieuRongMatTien + ' m';
            document.getElementById('khoangLuiSau').textContent = khoangLuiSauText;
            document.getElementById('dienTichSanSau').textContent = dienTichSanSau + ' m²';
            document.getElementById('soTangToiDa').textContent = soTang + ' tầng';
            document.getElementById('chieuCaoToiDaTaiCGXD').textContent = chieuCao.taiCGXD;
            document.getElementById('chieuCaoToiDaTaiDinhMai').textContent = chieuCao.taiDinhMai;
            document.getElementById('thongTinTangLung').textContent = thongTinTangLung;
            document.getElementById('doVuonBanCong').textContent = doVuonBanCongText;
            document.getElementById('dienTichBanCong').textContent = dienTichBanCong.toFixed(1) + ' m²';
            
            // Kiểm tra điều kiện lô đất nhỏ và hiển thị cảnh báo nếu cần
            const loDatNhoWarning = document.getElementById('loDatNhoWarning');
            const loDatNhoMessage = document.getElementById('loDatNhoMessage');
            
            if (dienTichDat < 36) {
                loDatNhoWarning.classList.remove('hidden');
                if (chieuRongMatTien < 3.0 || chieuSauDat < 3.0) {
                    loDatNhoMessage.innerHTML = `
                        <p>Lô đất của bạn có diện tích ${dienTichDat} m² với chiều rộng mặt tiền ${chieuRongMatTien} m và chiều sâu ${chieuSauDat} m.</p>
                        <p class="mt-1"><strong>Hạn chế:</strong> Chỉ được cải tạo, sửa chữa theo quy mô hiện trạng hoặc xây dựng mới với chiều cao tối đa tại CGXD 7,0m và chiều cao tại đỉnh mái không quá 9,0m.</p>
                    `;
                } else if (dienTichDat < 15) {
                    loDatNhoMessage.innerHTML = `
                        <p>Lô đất của bạn có diện tích ${dienTichDat} m² (nhỏ hơn 15m²).</p>
                        <p class="mt-1"><strong>Hạn chế:</strong> Chỉ được cải tạo, sửa chữa theo hiện trạng hoặc xây dựng mới với chiều cao tối đa tại đỉnh mái không quá 7,0m.</p>
                    `;
                } else {
                    loDatNhoMessage.innerHTML = `
                        <p>Lô đất của bạn có diện tích ${dienTichDat} m² (từ 15m² đến dưới 36m²).</p>
                        <p class="mt-1"><strong>Quy định:</strong> ${chieuRongLoGioi >= 6 ? 
                            'Với lộ giới ≥ 6m, chiều cao tối đa tại CGXD 11,6m và chiều cao tối đa tại đỉnh mái 13,6m.' : 
                            'Với lộ giới < 6m, chiều cao tối đa tại đỉnh mái 11,6m.'}</p>
                    `;
                }
            } else {
                loDatNhoWarning.classList.add('hidden');
            }
            
            // Hiển thị bảng khái toán
            document.getElementById('no-khai-toan').classList.add('hidden');
            document.getElementById('has-khai-toan').classList.remove('hidden');
            renderKhaiToanTable(khaiToan.khaiToanTable);
            
            // Tính và hiển thị chi phí
            const donGiaThietKe = parseFormattedNumber(document.getElementById('donGiaThietKe').value) || 250000;
            const donGiaPhanTho = parseFormattedNumber(document.getElementById('donGiaPhanTho').value) || 4000000;
            const donGiaHoanThien = parseFormattedNumber(document.getElementById('donGiaHoanThien').value) || 2500000;
            const donGiaNoiThat = parseFormattedNumber(document.getElementById('donGiaNoiThat').value) || 2000000;
            
            const chiPhiThietKe = khaiToan.tongDienTichThietKe * donGiaThietKe;
            const chiPhiPhanTho = khaiToan.tongDienTichXayDung * donGiaPhanTho;
            const chiPhiHoanThien = khaiToan.tongDienTichXayDung * donGiaHoanThien;
            const chiPhiNoiThat = khaiToan.tongDienTichXayDung * 0.85 * donGiaNoiThat;
            
            const tongChiPhi = chiPhiThietKe + chiPhiPhanTho + chiPhiHoanThien + chiPhiNoiThat;
            
            // Tính phần trăm của từng chi phí
            const percentThietKe = ((chiPhiThietKe / tongChiPhi) * 100).toFixed(1);
            const percentPhanTho = ((chiPhiPhanTho / tongChiPhi) * 100).toFixed(1);
            const percentHoanThien = ((chiPhiHoanThien / tongChiPhi) * 100).toFixed(1);
            const percentNoiThat = ((chiPhiNoiThat / tongChiPhi) * 100).toFixed(1);
            
            // Hiển thị lại các chi phí với phần trăm
            document.getElementById('chiPhiThietKe').innerHTML = `${formatCurrency(chiPhiThietKe)} <small class="text-gray-400">(${percentThietKe}%)</small>`;
            document.getElementById('chiPhiPhanTho').innerHTML = `${formatCurrency(chiPhiPhanTho)} <small class="text-gray-400">(${percentPhanTho}%)</small>`;
            document.getElementById('chiPhiHoanThien').innerHTML = `${formatCurrency(chiPhiHoanThien)} <small class="text-gray-400">(${percentHoanThien}%)</small>`;
            document.getElementById('chiPhiNoiThat').innerHTML = `${formatCurrency(chiPhiNoiThat)} <small class="text-gray-400">(${percentNoiThat}%)</small>`;
            document.getElementById('tongChiPhi').textContent = formatCurrency(tongChiPhi);
            
            // Chuyển đến tab kết quả tính toán
            switchToTab('ket-qua');
            
            // Hiển thị thông báo thành công
            showNotification('Đã tính toán thành công!', 'success');
        });

        // Initialize UI
        function initializeUI() {
            // Check initial lộ giới value
            updateTangLungAvailability(parseFloat(document.getElementById('chieuRongLoGioi').value) || 0);
            
            // Initialize currency format
            document.querySelectorAll('.currency-input').forEach(input => {
                const rawValue = input.value.replace(/\./g, '');
                if (rawValue && !isNaN(parseFloat(rawValue))) {
                    input.value = formatNumber(parseFloat(rawValue));
                }
            });
        }

        // Call initialization
        initializeUI();
    </script>
</body>
</html>

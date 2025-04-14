<html lang="vi">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Tư vấn xây dựng theo QĐ 56-2021</title>
    <link href="https://cdn.jsdelivr.net/npm/tailwindcss@2.2.19/dist/tailwind.min.css" rel="stylesheet">
    <link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/@fortawesome/fontawesome-free@6.4.0/css/all.min.css">
    <style>
        :root {
            --bg-dark: #121212;
            --bg-card: #1E1E1E;
            --bg-input: #2D2D2D;
            --text-primary: #E0E0E0;
            --text-secondary: #BBBBBB;
            --primary: #3B82F6;
            --primary-dark: #2563EB;
            --green: #10B981;
            --red: #EF4444;
            --border: #3F3F3F;
        }
        
        body {
            background-color: var(--bg-dark);
            color: var(--text-primary);
            font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Open Sans', 'Helvetica Neue', sans-serif;
        }
        
        .card {
            background-color: var(--bg-card);
            border: 1px solid var(--border);
            border-radius: 0.5rem;
        }
        
        .header-logo {
            max-height: 40px;
        }
        
        .form-input {
            background-color: var(--bg-input);
            border: 1px solid var(--border);
            color: var(--text-primary);
            border-radius: 0.375rem;
            padding: 0.75rem;
            width: 100%;
            font-size: 16px;
        }
        
        .form-input:focus {
            border-color: var(--primary);
            outline: none;
        }
        
        .form-label {
            color: var(--text-secondary);
            font-size: 0.875rem;
            margin-bottom: 0.25rem;
            display: block;
        }
        
        .btn-primary {
            background-color: var(--primary);
            color: white;
            padding: 0.75rem 1.5rem;
            border-radius: 0.375rem;
            font-weight: 500;
            width: 100%;
            font-size: 16px;
            transition: background-color 0.2s;
        }
        
        .btn-primary:hover {
            background-color: var(--primary-dark);
        }
        
        .section-title {
            font-size: 1.125rem;
            font-weight: 600;
            color: var(--primary);
            margin-bottom: 1rem;
            padding-bottom: 0.5rem;
            border-bottom: 1px solid var(--border);
        }
        
        /* Custom radio and checkbox styles */
        .radio-container, .checkbox-container {
            display: flex;
            align-items: center;
            margin-bottom: 0.75rem;
            cursor: pointer;
        }
        
        .custom-radio, .custom-checkbox {
            height: 1.25rem;
            width: 1.25rem;
            margin-right: 0.75rem;
            accent-color: var(--primary);
        }
        
        /* Navigation tabs */
        .nav-tabs {
            display: flex;
            border-bottom: 1px solid var(--border);
            margin-bottom: 1rem;
            overflow-x: auto;
            scrollbar-width: none;
        }
        
        .nav-tabs::-webkit-scrollbar {
            display: none;
        }
        
        .nav-tab {
            padding: 0.75rem 1rem;
            font-weight: 500;
            color: var(--text-secondary);
            border-bottom: 2px solid transparent;
            white-space: nowrap;
        }
        
        .nav-tab.active {
            color: var(--primary);
            border-bottom-color: var(--primary);
        }
        
        /* Tab content */
        .tab-content {
            display: none;
        }
        
        .tab-content.active {
            display: block;
        }
        
        /* Results */
        .result-section {
            margin-bottom: 1.5rem;
        }
        
        .result-title {
            font-weight: 600;
            color: var(--primary);
            margin-bottom: 0.5rem;
        }
        
        .result-row {
            display: flex;
            justify-content: space-between;
            padding: 0.5rem 0;
            border-bottom: 1px dashed var(--border);
        }
        
        .result-label {
            color: var(--text-secondary);
        }
        
        .result-value {
            font-weight: 500;
            color: var(--text-primary);
        }
        
        /* Khái toán table */
        .khaitoan-table {
            width: 100%;
            border-collapse: collapse;
            font-size: 0.875rem;
        }
        
        .khaitoan-table th {
            text-align: left;
            padding: 0.75rem;
            color: var(--text-secondary);
            border-bottom: 1px solid var(--border);
        }
        
        .khaitoan-table td {
            padding: 0.75rem;
            border-bottom: 1px solid var(--border);
        }
        
        .khaitoan-table tr:last-child td {
            border-bottom: none;
        }
        
        .total-row {
            background-color: var(--primary);
            color: white;
            font-weight: 600;
        }
        
        .total-row td {
            color: white !important;
        }
        
        /* Error message */
        .error-message {
            color: var(--red);
            font-size: 0.875rem;
            margin-top: 0.25rem;
            display: none;
        }
        
        /* Notification */
        .notification {
            position: fixed;
            bottom: 1rem;
            left: 1rem;
            right: 1rem;
            background-color: var(--bg-card);
            border-left: 4px solid var(--primary);
            padding: 1rem;
            border-radius: 0.375rem;
            box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
            z-index: 50;
            display: none;
        }
        
        .notification.error {
            border-left-color: var(--red);
        }
        
        .notification.success {
            border-left-color: var(--green);
        }
        
        /* Mobile bottom navigation */
        .bottom-nav {
            position: fixed;
            bottom: 0;
            left: 0;
            right: 0;
            background-color: var(--bg-card);
            display: flex;
            justify-content: space-around;
            padding: 0.5rem 0;
            border-top: 1px solid var(--border);
            z-index: 40;
        }
        
        .bottom-nav-item {
            display: flex;
            flex-direction: column;
            align-items: center;
            padding: 0.5rem;
            color: var(--text-secondary);
            font-size: 0.75rem;
        }
        
        .bottom-nav-item.active {
            color: var(--primary);
        }
        
        .bottom-nav-icon {
            font-size: 1.25rem;
            margin-bottom: 0.25rem;
        }
        
        /* Main content padding to account for bottom nav */
        .main-content {
            padding-bottom: 5rem;
        }
        
        /* Back to top button */
        .back-to-top {
            position: fixed;
            bottom: 5rem;
            right: 1rem;
            background-color: var(--primary);
            color: white;
            width: 2.5rem;
            height: 2.5rem;
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            cursor: pointer;
            z-index: 30;
            opacity: 0;
            transition: opacity 0.3s;
        }
        
        /* Hide elements with js-hidden class */
        .js-hidden {
            display: none;
        }
        
        /* Responsive table container */
        .table-container {
            overflow-x: auto;
        }
        
        /* Coefficient display in form */
        .coefficient {
            display: inline-block;
            background-color: var(--primary);
            color: white;
            font-size: 0.75rem;
            padding: 0.125rem 0.375rem;
            border-radius: 0.25rem;
            margin-left: 0.5rem;
        }
        
        /* Required field marker */
        .required::after {
            content: "*";
            color: var(--red);
            margin-left: 0.25rem;
        }
        
        /* Focus indicator for better accessibility */
        button:focus, input:focus, select:focus {
            outline: 2px solid var(--primary);
            outline-offset: 2px;
        }
        
        /* Construction option grid */
        .construction-option-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(200px, 1fr));
            gap: 0.75rem;
        }
        
        /* Disable scrolling when modal is open */
        body.modal-open {
            overflow: hidden;
        }
        
        /* Padding adjustments for better spacing */
        .content-padding {
            padding: 1rem;
        }
        
        @media (min-width: 640px) {
            .content-padding {
                padding: 1.5rem;
            }
        }
        
        /* Loader */
        .loader {
            border: 3px solid rgba(59, 130, 246, 0.3);
            border-radius: 50%;
            border-top: 3px solid var(--primary);
            width: 24px;
            height: 24px;
            animation: spin 1s linear infinite;
            display: inline-block;
            vertical-align: middle;
            margin-right: 0.5rem;
        }
        
        @keyframes spin {
            0% { transform: rotate(0deg); }
            100% { transform: rotate(360deg); }
        }
        
        /* Badge for conditions met */
        .condition-badge {
            display: inline-block;
            background-color: rgba(59, 130, 246, 0.2);
            color: var(--primary);
            font-size: 0.75rem;
            padding: 0.25rem 0.5rem;
            border-radius: 0.25rem;
            margin-top: 0.25rem;
            margin-right: 0.25rem;
        }
        
        /* Condition details section */
        .conditions-met {
            margin-top: 0.5rem;
            padding: 0.5rem;
            background-color: rgba(59, 130, 246, 0.1);
            border-radius: 0.375rem;
            font-size: 0.875rem;
        }
        
        .condition-item {
            display: flex;
            align-items: center;
            margin-bottom: 0.25rem;
        }
        
        .condition-icon {
            margin-right: 0.5rem;
            color: var(--green);
        }
        
        .condition-icon.not-met {
            color: var(--red);
        }
    </style>
</head>
<body>
    <!-- Header -->
    <header class="bg-gray-900 py-3 px-4 sticky top-0 z-10 shadow-md">
        <div class="flex items-center justify-between">
            <a href="https://vtzspaxe.com/" target="_blank" class="flex items-center">
                <img src="https://raw.githubusercontent.com/vtzai2024/TinhMatDoXayDung/main/LOGO%20VUONG%20NEN%20TRONG%20SUOT%20-chu%20trang-small.png" alt="VTZ Spaxe Logo" class="header-logo mr-2">
                <div>
                    <div class="text-white font-bold text-sm">VTZ Spaxe</div>
                    <div class="text-gray-400 text-xs">Thiết kế & Xây dựng</div>
                </div>
            </a>
            <div class="text-white font-bold text-sm md:text-base">Tư vấn xây dựng QĐ 56-2021</div>
        </div>
    </header>

    <!-- Main Content -->
    <div class="container mx-auto px-4 py-4 main-content">
        <!-- Navigation Tabs -->
        <div class="nav-tabs">
            <button class="nav-tab active" data-tab="input-tab">Nhập dữ liệu</button>
            <button class="nav-tab" data-tab="results-tab">Kết quả</button>
            <button class="nav-tab" data-tab="khaitoan-tab">Khái toán</button>
            <button class="nav-tab" data-tab="special-tab">Lô đất đặc biệt</button>
            <button class="nav-tab" data-tab="about-tab">Giới thiệu</button>
        </div>

        <!-- Tab Contents -->
        <div class="tab-contents">
            <!-- Input Tab -->
            <div id="input-tab" class="tab-content active">
                <form id="calculationForm">
                    <!-- Thông tin lô đất -->
                    <div class="card mb-5 content-padding">
                        <h2 class="section-title">
                            <i class="fas fa-info-circle mr-2"></i> Thông tin lô đất
                        </h2>
                        <div class="mb-4">
                            <label for="dienTichDat" class="form-label required">Diện tích lô đất (m²):</label>
                            <input type="number" id="dienTichDat" class="form-input" placeholder="Nhập diện tích lô đất" min="0" step="0.01">
                            <div id="dienTichDat-error" class="error-message">Vui lòng nhập diện tích lô đất</div>
                        </div>
                        <div class="mb-4">
                            <label for="chieuSauDat" class="form-label required">Chiều sâu lô đất (m):</label>
                            <input type="number" id="chieuSauDat" class="form-input" placeholder="Nhập chiều sâu lô đất" min="0" step="0.01">
                            <div id="chieuSauDat-error" class="error-message">Vui lòng nhập chiều sâu lô đất</div>
                        </div>
                        <div class="mb-4">
                            <label for="chieuRongLoGioi" class="form-label required">Chiều rộng lộ giới (m):</label>
                            <input type="number" id="chieuRongLoGioi" class="form-input" placeholder="Nhập chiều rộng lộ giới" min="0" step="0.01">
                            <div id="chieuRongLoGioi-error" class="error-message">Vui lòng nhập chiều rộng lộ giới</div>
                        </div>
                        <div class="mb-4">
                            <label for="chieuRongMatTien" class="form-label required">Chiều rộng mặt tiền (m):</label>
                            <input type="number" id="chieuRongMatTien" class="form-input" placeholder="Nhập chiều rộng mặt tiền" min="0" step="0.01">
                            <div id="chieuRongMatTien-error" class="error-message">Vui lòng nhập chiều rộng mặt tiền</div>
                        </div>
                        <div class="mt-4">
                            <p class="form-label">Điều kiện đặc biệt:</p>
                            <label class="checkbox-container">
                                <input type="checkbox" id="quanTrungTam" class="custom-checkbox">
                                <span>Thuộc Quận trung tâm hoặc Trung tâm cấp quận</span>
                            </label>
                            <label class="checkbox-container">
                                <input type="checkbox" id="trucDuongThuongMai" class="custom-checkbox">
                                <span>Thuộc trục đường thương mại - dịch vụ</span>
                            </label>
                            <label class="checkbox-container">
                                <input type="checkbox" id="matTienTren8m" class="custom-checkbox">
                                <span>Có chiều rộng mặt tiền > 8,0m</span>
                            </label>
                            <label class="checkbox-container">
                                <input type="checkbox" id="loDatGoc" class="custom-checkbox">
                                <span>Lô đất góc (tiếp giáp hai đường)</span>
                            </label>
                        </div>
                    </div>

                    <!-- Diện tích xây dựng -->
                    <div class="card mb-5 content-padding">
                        <h2 class="section-title">
                            <i class="fas fa-building mr-2"></i> Diện tích xây dựng
                        </h2>
                        
                        <!-- Tầng hầm -->
                        <div class="mb-5">
                            <h3 class="text-white text-base font-semibold mb-2">
                                <i class="fas fa-arrow-down mr-2"></i> Tầng hầm
                            </h3>
                            <div class="mb-3">
                                <label class="radio-container">
                                    <input type="radio" name="tangHam" value="none" class="custom-radio" checked>
                                    <span>Không có tầng hầm</span>
                                </label>
                                <label class="radio-container">
                                    <input type="radio" name="tangHam" value="ham" class="custom-radio">
                                    <span>Có tầng hầm</span>
                                </label>
                            </div>
                            <div id="tangHamOptions" class="pl-4 js-hidden">
                                <p class="text-gray-400 text-sm mb-2">Chọn độ sâu hầm:</p>
                                <div class="grid grid-cols-1 sm:grid-cols-2 gap-2 mb-3">
                                    <label class="radio-container">
                                        <input type="radio" name="doSauHam" id="doSau1" value="1.5" class="custom-radio">
                                        <span>Sâu 1.0m - 1.3m <span class="coefficient">150%</span></span>
                                    </label>
                                    <label class="radio-container">
                                        <input type="radio" name="doSauHam" id="doSau2" value="1.7" class="custom-radio">
                                        <span>Sâu 1.3m - 1.7m <span class="coefficient">170%</span></span>
                                    </label>
                                    <label class="radio-container">
                                        <input type="radio" name="doSauHam" id="doSau3" value="2.0" class="custom-radio">
                                        <span>Sâu 1.7m - 2.0m <span class="coefficient">200%</span></span>
                                    </label>
                                    <label class="radio-container">
                                        <input type="radio" name="doSauHam" id="doSau4" value="2.2" class="custom-radio">
                                        <span>Sâu trên 2.0m <span class="coefficient">220%</span></span>
                                    </label>
                                </div>
                                <label class="checkbox-container">
                                    <input type="checkbox" id="hamNho" class="custom-checkbox">
                                    <span>Hầm có diện tích sử dụng < 70m² <span class="coefficient">+20%</span></span>
                                </label>
                            </div>
                        </div>
                        
                        <!-- Móng -->
                        <div class="mb-5">
                            <h3 class="text-white text-base font-semibold mb-2">
                                <i class="fas fa-arrow-down mr-2"></i> Móng
                            </h3>
                            <div class="grid grid-cols-1 sm:grid-cols-2 gap-2">
                                <label class="radio-container">
                                    <input type="radio" name="loaiMong" id="mongDon" value="0.3" class="custom-radio" checked>
                                    <span>Móng đơn <span class="coefficient">30%</span></span>
                                </label>
                                <label class="radio-container">
                                    <input type="radio" name="loaiMong" id="mongCoc" value="0.5" class="custom-radio">
                                    <span>Móng cọc <span class="coefficient">50%</span></span>
                                </label>
                                <label class="radio-container">
                                    <input type="radio" name="loaiMong" id="mongBang" value="0.5" class="custom-radio">
                                    <span>Móng băng <span class="coefficient">50%</span></span>
                                </label>
                                <label class="radio-container">
                                    <input type="radio" name="loaiMong" id="mongBe" value="0.8" class="custom-radio">
                                    <span>Móng bè <span class="coefficient">80%</span></span>
                                </label>
                            </div>
                        </div>
                        
                        <!-- Mái -->
                        <div class="mb-3">
                            <h3 class="text-white text-base font-semibold mb-2">
                                <i class="fas fa-home mr-2"></i> Mái
                            </h3>
                            <div class="grid grid-cols-1 sm:grid-cols-2 gap-2">
                                <label class="radio-container">
                                    <input type="radio" name="loaiMai" id="maiBTCT" value="0.5" class="custom-radio" checked>
                                    <span>Mái BTCT <span class="coefficient">50%</span></span>
                                </label>
                                <label class="radio-container">
                                    <input type="radio" name="loaiMai" id="maiTon" value="0.3" class="custom-radio">
                                    <span>Mái tôn <span class="coefficient">30%</span></span>
                                </label>
                                <label class="radio-container">
                                    <input type="radio" name="loaiMai" id="maiNgoi" value="0.7" class="custom-radio">
                                    <span>Mái ngói kèo sắt <span class="coefficient">70%</span></span>
                                </label>
                                <label class="radio-container">
                                    <input type="radio" name="loaiMai" id="maiXienBTCT" value="0.8" class="custom-radio">
                                    <span>Mái xiên BTCT <span class="coefficient">80%</span></span>
                                </label>
                            </div>
                        </div>
                    </div>

                    <!-- Đơn giá xây dựng -->
                    <div class="card mb-5 content-padding">
                        <h2 class="section-title">
                            <i class="fas fa-dollar-sign mr-2"></i> Đơn giá xây dựng
                        </h2>
                        <div class="mb-4">
                            <label for="donGiaThietKe" class="form-label">Đơn giá thiết kế (VNĐ/m²):</label>
                            <input type="text" id="donGiaThietKe" class="form-input" value="250.000" placeholder="VNĐ/m²">
                        </div>
                        <div class="mb-4">
                            <label for="donGiaPhanTho" class="form-label">Đơn giá phần thô (VNĐ/m²):</label>
                            <input type="text" id="donGiaPhanTho" class="form-input" value="4.000.000" placeholder="VNĐ/m²">
                        </div>
                        <div class="mb-4">
                            <label for="donGiaHoanThien" class="form-label">Đơn giá hoàn thiện (VNĐ/m²):</label>
                            <input type="text" id="donGiaHoanThien" class="form-input" value="2.500.000" placeholder="VNĐ/m²">
                        </div>
                        <div class="mb-4">
                            <label for="donGiaNoiThat" class="form-label">Đơn giá nội thất (VNĐ/m²):</label>
                            <input type="text" id="donGiaNoiThat" class="form-input" value="2.000.000" placeholder="VNĐ/m²">
                        </div>
                    </div>

                    <!-- Tùy chọn bổ sung -->
                    <div class="card mb-5 content-padding">
                        <h2 class="section-title">
                            <i class="fas fa-cog mr-2"></i> Tùy chọn bổ sung
                        </h2>
                        <label class="checkbox-container">
                            <input type="checkbox" id="coTangLung" class="custom-checkbox" checked>
                            <span>Có tầng lửng</span>
                        </label>
                        <label class="checkbox-container">
                            <input type="checkbox" id="coTangDinhMai" class="custom-checkbox" checked disabled>
                            <span>Có tầng đỉnh mái <span class="bg-primary text-white text-xs px-2 py-0.5 rounded">Bắt buộc</span></span>
                        </label>
                        <label class="checkbox-container">
                            <input type="checkbox" id="coSanThuong" class="custom-checkbox" checked>
                            <span>Có sân thượng</span>
                        </label>
                        <label class="checkbox-container">
                            <input type="checkbox" id="coMaiBTCT" class="custom-checkbox" checked>
                            <span>Có mái BTCT</span>
                        </label>
                    </div>

                    <!-- Calculate Button -->
                    <button type="button" id="tinhToanBtn" class="btn-primary mb-4">
                        <span id="tinhToanText">Tính toán</span>
                        <span id="tinhToanLoader" class="loader hidden"></span>
                    </button>
                </form>
            </div>

            <!-- Results Tab -->
            <div id="results-tab" class="tab-content">
                <div class="card mb-5 content-padding">
                    <h2 class="section-title">
                        <i class="fas fa-calculator mr-2"></i> Kết quả tính toán
                    </h2>
                    
                    <div class="result-section">
                        <h3 class="result-title"><i class="fas fa-ruler-combined mr-2"></i> Thông số cơ bản</h3>
                        <div class="result-row">
                            <span class="result-label">Diện tích lô đất:</span>
                            <span class="result-value" id="dienTichLoDat">--</span>
                        </div>
                        <div class="result-row">
                            <span class="result-label">Mật độ xây dựng tối đa:</span>
                            <span class="result-value" id="matDoXayDung">--</span>
                        </div>
                        <div class="result-row">
                            <span class="result-label">Diện tích được xây dựng:</span>
                            <span class="result-value" id="dienTichXayDung">--</span>
                        </div>
                    </div>
                    
                    <div class="result-section">
                        <h3 class="result-title"><i class="fas fa-arrows-alt-h mr-2"></i> Khoảng lùi</h3>
                        <div class="result-row">
                            <span class="result-label">Khoảng lùi phía sau:</span>
                            <span class="result-value" id="khoangLuiSau">--</span>
                        </div>
                        <div class="result-row">
                            <span class="result-label">Diện tích sân sau:</span>
                            <span class="result-value" id="dienTichSanSau">--</span>
                        </div>
                    </div>
                    
                    <div class="result-section">
                        <h3 class="result-title"><i class="fas fa-building mr-2"></i> Chiều cao và số tầng</h3>
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
                        <div id="conditionsMet" class="conditions-met js-hidden">
                            <p class="text-sm font-semibold mb-2">Điều kiện cộng tầng đã đáp ứng:</p>
                            <div id="conditionsList"></div>
                        </div>
                        <div class="result-row">
                            <span class="result-label">Tầng lửng:</span>
                            <span class="result-value" id="thongTinTangLung">--</span>
                        </div>
                    </div>
                    
                    <div class="result-section">
                        <h3 class="result-title"><i class="fas fa-home mr-2"></i> Ban công và ô văng</h3>
                        <div class="result-row">
                            <span class="result-label">Độ vươn tối đa của ban công:</span>
                            <span class="result-value" id="doVuonBanCong">--</span>
                        </div>
                        <div class="result-row">
                            <span class="result-label">Diện tích ban công:</span>
                            <span class="result-value" id="dienTichBanCong">--</span>
                        </div>
                    </div>
                    
                    <div class="mt-4 p-3 bg-yellow-900 bg-opacity-25 border-l-4 border-yellow-500">
                        <p class="text-yellow-300 text-sm">
                            <i class="fas fa-exclamation-triangle mr-2"></i>
                            <strong>Lưu ý:</strong> Kết quả tính toán chỉ mang tính tham khảo theo QĐ 56-2021. Vui lòng liên hệ cơ quan có thẩm quyền để được hướng dẫn chi tiết.
                        </p>
                    </div>
                </div>
            </div>

            <!-- Khái toán Tab -->
            <div id="khaitoan-tab" class="tab-content">
                <div class="card mb-5 content-padding">
                    <h2 class="section-title">
                        <i class="fas fa-file-invoice-dollar mr-2"></i> Khái toán chi phí xây dựng
                    </h2>
                    
                    <div class="table-container mb-4">
                        <table class="khaitoan-table" id="khaiToanTable">
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
                                <tr>
                                    <td colspan="6" class="text-center py-4 text-gray-400">
                                        Nhập thông tin và nhấn "Tính toán" để xem kết quả
                                    </td>
                                </tr>
                            </tbody>
                        </table>
                    </div>
                    
                    <div class="bg-blue-900 bg-opacity-25 p-4 rounded-lg space-y-3">
                        <div class="flex justify-between items-center">
                            <span class="text-gray-300">Chi phí thiết kế:</span>
                            <span id="chiPhiThietKe" class="font-semibold text-blue-400">--</span>
                        </div>
                        <div class="flex justify-between items-center">
                            <span class="text-gray-300">Chi phí phần thô:</span>
                            <span id="chiPhiPhanTho" class="font-semibold text-blue-400">--</span>
                        </div>
                        <div class="flex justify-between items-center">
                            <span class="text-gray-300">Chi phí hoàn thiện:</span>
                            <span id="chiPhiHoanThien" class="font-semibold text-blue-400">--</span>
                        </div>
                        <div class="flex justify-between items-center">
                            <span class="text-gray-300">Chi phí nội thất:</span>
                            <span id="chiPhiNoiThat" class="font-semibold text-blue-400">--</span>
                        </div>
                    </div>
                    
                    <div class="flex justify-between items-center mt-4 p-3 bg-green-600 rounded-lg">
                        <span class="font-bold text-white">Tổng chi phí:</span>
                        <span id="tongChiPhi" class="font-bold text-white">--</span>
                    </div>
                </div>
            </div>

            <!-- Special Plot Tab -->
            <div id="special-tab" class="tab-content">
                <div class="card mb-5 content-padding">
                    <h2 class="section-title">
                        <i class="fas fa-map-marker-alt mr-2"></i> Lô đất có vị trí đặc biệt
                    </h2>
                    
                    <p class="mb-4 text-gray-300">
                        Lô đất có vị trí đặc biệt là lô đất có vị trí tại góc giao của hai hoặc ba đường (hoặc hẻm) 
                        hoặc tiếp giáp hai đường (hoặc hẻm) có quy định khác nhau về tầng cao.
                    </p>
                    
                    <h3 class="font-semibold text-blue-400 mb-2">Trường hợp lô đất tại góc giao hai hoặc ba đường có quy định khác nhau về tầng cao:</h3>
                    
                    <ul class="list-disc pl-5 space-y-2 mb-4 text-gray-300">
                        <li>
                            <strong>Nếu chiều rộng lô đất (tại vị trí tiếp giáp ranh lộ giới) nhỏ hơn 3,0m quay về phía đường lớn</strong> 
                            thì các chỉ tiêu quy hoạch kiến trúc được xác định theo quy định đối với đường nhỏ
                        </li>
                        <li>
                            <strong>Nếu chiều rộng lô đất (tại vị trí tiếp giáp ranh lộ giới) tối thiểu 3,0m quay về phía đường lớn</strong> 
                            thì được áp dụng quy định tầng cao đối với đường lớn
                        </li>
                    </ul>
                    
                    <div class="flex justify-center mb-4">
                        <img src="https://raw.githubusercontent.com/vtzai2024/TinhMatDoXayDung/main/LOGO%20VUONG%20NEN%20TRONG%20SUOT%20-chu%20trang-small.png" alt="Minh họa lô đất góc" class="max-w-full h-auto">
                        <p class="text-center text-sm text-gray-400 mt-1">Minh họa lô đất góc tiếp giáp hai đường</p>
                    </div>
                    
                    <h3 class="font-semibold text-blue-400 mb-2">Đối với trường hợp lô đất tiếp giáp hai đường (hoặc hẻm):</h3>
                    
                    <p class="mb-4 text-gray-300">
                        Với lô đất tiếp giáp hai đường (hoặc hẻm) có quy định khác nhau về tầng cao, 
                        thì áp dụng quy định tầng cao đối với đường (hoặc hẻm) mà lô đất tiếp giáp với chiều dài lớn hơn.
                    </p>
                    
                    <div class="mt-4 p-3 bg-blue-900 bg-opacity-25 rounded">
                        <p class="text-sm text-gray-300">
                            <i class="fas fa-info-circle mr-2 text-blue-400"></i>
                            <strong>Lưu ý:</strong> Khi nhập dữ liệu, hãy đánh dấu vào ô "Lô đất góc (tiếp giáp hai đường)" 
                            nếu lô đất của bạn thuộc trường hợp đặc biệt. Hệ thống sẽ tính toán dựa trên chiều rộng lộ giới lớn nhất bạn nhập vào.
                        </p>
                    </div>
                </div>
            </div>

            <!-- About Tab -->
            <div id="about-tab" class="tab-content">
                <div class="card mb-5 content-padding">
                    <h2 class="section-title">
                        <i class="fas fa-info-circle mr-2"></i> Giới thiệu
                    </h2>
                    
                    <div class="mb-4 flex flex-col items-center">
                        <a href="https://vtzspaxe.com/" target="_blank">
                            <img src="https://raw.githubusercontent.com/vtzai2024/TinhMatDoXayDung/main/LOGO%20VUONG%20NEN%20TRONG%20SUOT%20-chu%20trang-small.png" alt="VTZ Spaxe Logo" class="h-24 w-24 mb-3">
                        </a>
                        <h3 class="text-lg font-semibold text-center">Công ty TNHH Thiết kế và xây dựng VTZ Spaxe</h3>
                        <p class="text-gray-400 text-sm text-center mt-1">TIÊN PHONG - TẬN TÂM - TRÁCH NHIỆM - TRUNG THỰC - TRÍ TUỆ</p>
                    </div>
                    
                    <p class="mb-3 text-gray-300">
                        Ứng dụng này giúp tính toán các thông số xây dựng theo Quyết định số 56/2021/QĐ-UBND của UBND TP. Hồ Chí Minh, 
                        bao gồm mật độ xây dựng, chiều cao, số tầng, khoảng lùi và khái toán chi phí xây dựng.
                    </p>
                    
                    <p class="mb-3 text-gray-300">
                        Đây là công cụ tham khảo giúp chủ đầu tư có thông tin sơ bộ về quy định xây dựng và chi phí dự kiến 
                        trước khi tiến hành thiết kế và xây dựng.
                    </p>
                    
                    <div class="mt-4 p-3 bg-blue-900 bg-opacity-25 rounded">
                        <p class="text-sm text-gray-300">
                            <i class="fas fa-envelope mr-2 text-blue-400"></i>
                            <strong>Liên hệ tư vấn:</strong><br>
                            Để được tư vấn chi tiết, vui lòng liên hệ với chúng tôi qua:<br>
                            Website: <a href="https://vtzspaxe.com/" target="_blank" class="text-blue-400">vtzspaxe.com</a>
                        </p>
                    </div>
                </div>
            </div>
        </div>
    </div>

    <!-- Bottom Navigation -->
    <nav class="bottom-nav">
        <a href="#" class="bottom-nav-item active" data-tab="input-tab">
            <span class="bottom-nav-icon"><i class="fas fa-keyboard"></i></span>
            <span>Nhập dữ liệu</span>
        </a>
        <a href="#" class="bottom-nav-item" data-tab="results-tab">
            <span class="bottom-nav-icon"><i class="fas fa-calculator"></i></span>
            <span>Kết quả</span>
        </a>
        <a href="#" class="bottom-nav-item" data-tab="khaitoan-tab">
            <span class="bottom-nav-icon"><i class="fas fa-file-invoice-dollar"></i></span>
            <span>Khái toán</span>
        </a>
        <a href="#" class="bottom-nav-item" data-tab="special-tab">
            <span class="bottom-nav-icon"><i class="fas fa-info-circle"></i></span>
            <span>Thông tin</span>
        </a>
    </nav>

    <!-- Back to Top Button -->
    <button class="back-to-top" id="backToTop">
        <i class="fas fa-arrow-up"></i>
    </button>

    <!-- Notification -->
    <div id="notification" class="notification">
        <span id="notificationMessage"></span>
    </div>

    <!-- Footer -->
    <footer class="mt-4 py-4 px-4 text-center text-sm text-gray-500 border-t border-gray-800">
        <p>© 2023-2025 - Ứng dụng được phát minh bởi công ty TNHH Thiết kế và xây dựng VTZ Spaxe</p>
        <p class="mt-1">Tư vấn xây dựng theo QĐ 56-2021/QĐ-UBND</p>
    </footer>

    <script>
        document.addEventListener('DOMContentLoaded', function() {
            // Show/hide sections based on radio selection
            const tangHamRadios = document.querySelectorAll('input[name="tangHam"]');
            const tangHamOptions = document.getElementById('tangHamOptions');
            
            tangHamRadios.forEach(radio => {
                radio.addEventListener('change', function() {
                    if (this.value === 'ham') {
                        tangHamOptions.classList.remove('js-hidden');
                        // Ensure a default option is selected
                        if (!document.querySelector('input[name="doSauHam"]:checked')) {
                            document.getElementById('doSau1').checked = true;
                        }
                    } else {
                        tangHamOptions.classList.add('js-hidden');
                    }
                });
            });
            
            // Ensure tangHamOptions is hidden by default (if "none" is selected)
            if (document.querySelector('input[name="tangHam"][value="none"]').checked) {
                tangHamOptions.classList.add('js-hidden');
            }
            
            // Update mat tien checkbox based on input
            const chieuRongMatTienInput = document.getElementById('chieuRongMatTien');
            const matTienTren8mCheckbox = document.getElementById('matTienTren8m');
            
            chieuRongMatTienInput.addEventListener('input', function() {
                const value = parseFloat(this.value) || 0;
                matTienTren8mCheckbox.checked = value > 8.0;
            });
            
            // Update tang lung availability based on lo gioi
            const chieuRongLoGioiInput = document.getElementById('chieuRongLoGioi');
            const coTangLungCheckbox = document.getElementById('coTangLung');
            
            chieuRongLoGioiInput.addEventListener('input', function() {
                const value = parseFloat(this.value) || 0;
                coTangLungCheckbox.disabled = value < 6;
                if (value < 6) {
                    coTangLungCheckbox.checked = false;
                }
            });
            
            // Format currency inputs
            const currencyInputs = ['donGiaThietKe', 'donGiaPhanTho', 'donGiaHoanThien', 'donGiaNoiThat'];
            
            currencyInputs.forEach(id => {
                const input = document.getElementById(id);
                
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
            
            // Tab navigation
            const tabButtons = document.querySelectorAll('[data-tab]');
            
            tabButtons.forEach(button => {
                button.addEventListener('click', function() {
                    const tabId = this.getAttribute('data-tab');
                    
                    // Update tab buttons
                    document.querySelectorAll('.nav-tab').forEach(tab => {
                        tab.classList.remove('active');
                    });
                    document.querySelectorAll('.nav-tab[data-tab="' + tabId + '"]').forEach(tab => {
                        tab.classList.add('active');
                    });
                    
                    // Update bottom nav buttons
                    document.querySelectorAll('.bottom-nav-item').forEach(item => {
                        item.classList.remove('active');
                    });
                    document.querySelectorAll('.bottom-nav-item[data-tab="' + tabId + '"]').forEach(item => {
                        item.classList.add('active');
                    });
                    
                    // Show selected tab content
                    document.querySelectorAll('.tab-content').forEach(content => {
                        content.classList.remove('active');
                    });
                    document.getElementById(tabId).classList.add('active');
                    
                    // Scroll to top when switching tabs
                    window.scrollTo(0, 0);
                });
            });
            
            // Back to top button
            const backToTopButton = document.getElementById('backToTop');
            
            window.addEventListener('scroll', function() {
                if (window.pageYOffset > 300) {
                    backToTopButton.style.opacity = '1';
                } else {
                    backToTopButton.style.opacity = '0';
                }
            });
            
            backToTopButton.addEventListener('click', function() {
                window.scrollTo({
                    top: 0,
                    behavior: 'smooth'
                });
            });
            
            // Helper Functions
            function formatNumber(number) {
                return number.toString().replace(/\B(?=(\d{3})+(?!\d))/g, ".");
            }
            
            function formatCurrency(number) {
                return formatNumber(Math.round(number)) + ' VNĐ';
            }
            
            function parseFormattedNumber(formattedNumber) {
                if (typeof formattedNumber === 'string') {
                    return parseInt(formattedNumber.replace(/\./g, ''));
                }
                return formattedNumber;
            }
            
            function showError(fieldId, message) {
                const errorElement = document.getElementById(`${fieldId}-error`);
                if (errorElement) {
                    errorElement.textContent = message;
                    errorElement.style.display = 'block';
                    document.getElementById(fieldId).classList.add('border-red-500');
                }
            }
            
            function hideError(fieldId) {
                const errorElement = document.getElementById(`${fieldId}-error`);
                if (errorElement) {
                    errorElement.style.display = 'none';
                    document.getElementById(fieldId).classList.remove('border-red-500');
                }
            }
            
            function showNotification(message, type = 'info') {
                const notification = document.getElementById('notification');
                const notificationMessage = document.getElementById('notificationMessage');
                
                // Set message and type
                notificationMessage.textContent = message;
                notification.className = 'notification';
                notification.classList.add(type);
                
                // Show notification
                notification.style.display = 'block';
                
                // Hide after 3 seconds
                setTimeout(() => {
                    notification.style.display = 'none';
                }, 3000);
            }
            
            // Calculation Functions
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
            
            function tinhKhoangLuiSau(chieuSauDat) {
                if (chieuSauDat >= 16) {
                    return 2;
                } else if (chieuSauDat >= 9) {
                    return 1;
                } else {
                    return 0.5;
                }
            }
            
            function getKhoangLuiSauText(chieuSauDat) {
                if (chieuSauDat >= 16) {
                    return "Tối thiểu 2m";
                } else if (chieuSauDat >= 9) {
                    return "Tối thiểu 1m";
                } else {
                    return "Khuyến khích tạo khoảng trống phía sau";
                }
            }
            
            // New function to get conditions for additional floors
            function getDieuKienCongTang(chieuRongLoGioi, quanTrungTam, trucDuongThuongMai, matTienTren8m) {
                const dieuKien = [];
                let soTangCongThem = 0;
                
                if (chieuRongLoGioi < 3.5) {
                    return { dieuKien, soTangCongThem };
                }
                
                if (quanTrungTam) {
                    dieuKien.push({
                        text: "Thuộc Quận trung tâm hoặc Trung tâm cấp quận",
                        met: true
                    });
                    soTangCongThem++;
                } else {
                    dieuKien.push({
                        text: "Thuộc Quận trung tâm hoặc Trung tâm cấp quận",
                        met: false
                    });
                }
                
                if (trucDuongThuongMai && chieuRongLoGioi >= 16) {
                    dieuKien.push({
                        text: "Thuộc trục đường thương mại - dịch vụ",
                        met: true
                    });
                    soTangCongThem++;
                } else if (chieuRongLoGioi >= 16) {
                    dieuKien.push({
                        text: "Thuộc trục đường thương mại - dịch vụ",
                        met: false
                    });
                }
                
                if (matTienTren8m) {
                    dieuKien.push({
                        text: "Có chiều rộng mặt tiền > 8,0m",
                        met: true
                    });
                    soTangCongThem++;
                } else {
                    dieuKien.push({
                        text: "Có chiều rộng mặt tiền > 8,0m",
                        met: false
                    });
                }
                
                return { dieuKien, soTangCongThem };
            }
            
            function tinhSoTangToiDa(chieuRongLoGioi, quanTrungTam, trucDuongThuongMai, matTienTren8m) {
                let soTangCoBan = 0;
                
                // Xác định số tầng cơ bản theo chiều rộng lộ giới
                if (chieuRongLoGioi >= 25) {
                    soTangCoBan = 6;
                } else if (chieuRongLoGioi >= 16) {
                    soTangCoBan = 5;
                } else if (chieuRongLoGioi >= 6) {
                    soTangCoBan = 4;
                } else if (chieuRongLoGioi >= 3.5) {
                    soTangCoBan = 3;
                } else {
                    soTangCoBan = 3;
                    // Không cộng thêm
                }
                
                // Lấy thông tin về điều kiện cộng tầng
                const { dieuKien, soTangCongThem } = getDieuKienCongTang(chieuRongLoGioi, quanTrungTam, trucDuongThuongMai, matTienTren8m);
                
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
            
            // Fixed function to correctly calculate maximum height at roof peak
            function tinhChieuCaoToiDa(chieuRongLoGioi, quanTrungTam, trucDuongThuongMai, matTienTren8m) {
                let chieuCaoTaiCGXD = ""; // Chiều cao tại chỉ giới xây dựng
                let chieuCaoTaiDinhMai = ""; // Chiều cao tại đỉnh mái
                let chieuCaoCoBan = ""; // Chiều cao cơ bản khi không có cộng tầng
                
                // Lấy thông tin về điều kiện cộng tầng
                const { dieuKien, soTangCongThem } = getDieuKienCongTang(chieuRongLoGioi, quanTrungTam, trucDuongThuongMai, matTienTren8m);
                
                // Có điều kiện cộng tầng hay không
                const coDieuKienCongTang = soTangCongThem > 0;
                
                // Xác định chiều cao theo Bảng 3 của Phụ lục 18
                if (chieuRongLoGioi >= 25) {
                    chieuCaoTaiCGXD = "25,0m";
                    chieuCaoCoBan = "25,0m";
                    chieuCaoTaiDinhMai = coDieuKienCongTang ? "27,0m" : "25,0m";
                } else if (chieuRongLoGioi >= 16) {
                    chieuCaoTaiCGXD = "21,6m";
                    chieuCaoCoBan = "23,6m";
                    chieuCaoTaiDinhMai = coDieuKienCongTang ? "27,0m" : "23,6m";
                } else if (chieuRongLoGioi >= 6) {
                    chieuCaoTaiCGXD = "17,0m";
                    chieuCaoCoBan = "19,0m";
                    chieuCaoTaiDinhMai = coDieuKienCongTang ? "22,4m" : "19,0m";
                } else if (chieuRongLoGioi >= 3.5) {
                    chieuCaoTaiCGXD = "11,6m";
                    chieuCaoCoBan = "13,6m";
                    chieuCaoTaiDinhMai = coDieuKienCongTang ? "15,6m" : "13,6m";
                } else {
                    chieuCaoTaiCGXD = "Không quy định riêng";
                    chieuCaoCoBan = "11,6m";
                    chieuCaoTaiDinhMai = "11,6m"; // Không có cộng tầng
                }
                
                return {
                    taiCGXD: chieuCaoTaiCGXD,
                    taiDinhMai: chieuCaoTaiDinhMai,
                    chieuCaoCoBan: chieuCaoCoBan,
                    dieuKien: dieuKien,
                    coDieuKienCongTang: coDieuKienCongTang
                };
            }
            
            function xacDinhTangLung(chieuRongLoGioi) {
                if (chieuRongLoGioi >= 6) {
                    if (chieuRongLoGioi >= 25) {
                        return "Cho phép có tầng lửng, tổng chiều cao tầng 1 (bao gồm tầng lửng) tối đa 7,0m";
                    } else if (chieuRongLoGioi >= 16) {
                        return "Cho phép có tầng lửng, tổng chiều cao tầng 1 (bao gồm tầng lửng) tối đa 7,0m";
                    } else {
                        return "Cho phép có tầng lửng, tổng chiều cao tầng 1 (bao gồm tầng lửng) tối đa 5,8m";
                    }
                } else {
                    return "Không được phép có tầng lửng (chiều rộng lộ giới < 6m)";
                }
            }
            
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
            
            function getDoVuonBanCongText(chieuRongLoGioi) {
                let doVuon = tinhDoVuonBanCong(chieuRongLoGioi);
                if (doVuon === 0) {
                    return "0m (không được phép)";
                } else {
                    return doVuon.toFixed(1) + "m";
                }
            }
            
            function tinhDienTichBanCong(chieuRongLoGioi, chieuRongMatTien, soTang) {
                const doVuonBanCong = tinhDoVuonBanCong(chieuRongLoGioi);
                // Tính số tầng có ban công (từ tầng 1 trở lên)
                const soTangCoBanCong = soTang > 0 ? soTang - 1 : 0;
                return doVuonBanCong * chieuRongMatTien * soTangCoBanCong;
            }
            
            function tinhKhaiToanChiPhi(dienTichDat, soTang, matDoXayDung, chieuRongLoGioi, chieuRongMatTien, chieuSauDat) {
                // Lấy trạng thái checkbox và radio buttons
                const coTangLung = document.getElementById('coTangLung').checked && !document.getElementById('coTangLung').disabled;
                const coTangDinhMai = document.getElementById('coTangDinhMai').checked;
                const coSanThuong = document.getElementById('coSanThuong').checked;
                const coMaiBTCT = document.getElementById('coMaiBTCT').checked;
                
                // Lấy thông tin từ phần diện tích xây dựng
                const coTangHam = document.querySelector('input[name="tangHam"]:checked').value === 'ham';
                const doSauHam = coTangHam ? parseFloat(document.querySelector('input[name="doSauHam"]:checked')?.value || 0) : 0;
                const hamNho = document.getElementById('hamNho').checked;
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
                
                // Thêm hàng tổng
                khaiToanTable.push({
                    stt: '',
                    hangMuc: 'Tổng',
                    dienTichDat: '',
                    heSo: '',
                    dienTichXD: tongDienTichXayDung
                });
                
                return {
                    khaiToanTable: khaiToanTable,
                    tongDienTichThietKe: tongDienTichThietKe,
                    tongDienTichXayDung: tongDienTichXayDung
                };
            }
            
            function renderKhaiToanTable(khaiToanTable) {
                const tableBody = document.getElementById('khaiToanBody');
                tableBody.innerHTML = '';
                
                // Thêm các hàng vào bảng
                khaiToanTable.forEach((item, index) => {
                    const row = document.createElement('tr');
                    
                    // Đánh dấu hàng tổng cộng
                    if (item.hangMuc === 'Tổng') {
                        row.classList.add('total-row');
                    }
                    
                    // Thêm cột STT
                    const sttCell = document.createElement('td');
                    sttCell.textContent = item.stt;
                    row.appendChild(sttCell);
                    
                    // Thêm cột Hạng mục
                    const hangMucCell = document.createElement('td');
                    hangMucCell.textContent = item.hangMuc;
                    row.appendChild(hangMucCell);
                    
                    // Thêm cột Diện tích cơ sở
                    const dienTichDatCell = document.createElement('td');
                    dienTichDatCell.textContent = item.dienTichDat ? item.dienTichDat.toFixed(1) : '';
                    row.appendChild(dienTichDatCell);
                    
                    // Thêm cột Hệ số
                    const heSoCell = document.createElement('td');
                    heSoCell.textContent = item.heSo !== '' ? item.heSo : '';
                    row.appendChild(heSoCell);
                    
                    // Thêm cột Diện tích XD
                    const dienTichXDCell = document.createElement('td');
                    dienTichXDCell.textContent = item.dienTichXD ? item.dienTichXD.toFixed(1) : '';
                    row.appendChild(dienTichXDCell);
                    
                    // Thêm cột Xây (checkbox)
                    const xayCell = document.createElement('td');
                    if (item.hangMuc !== 'Tổng') {
                        if (item.hangMuc === 'Tầng đỉnh mái') {
                            // Nếu là tầng đỉnh mái thì đánh dấu là bắt buộc
                            xayCell.innerHTML = '<div class="bg-blue-600 text-xs text-white px-1 py-0.5 rounded text-center">BT</div>';
                        } else {
                            // Checkbox và lưu trữ thông tin hàng cho tính toán
                            const checkbox = document.createElement('input');
                            checkbox.type = 'checkbox';
                            checkbox.className = 'build-checkbox custom-checkbox';
                            checkbox.checked = true;
                            checkbox.dataset.dienTichXD = item.dienTichXD;
                            checkbox.dataset.dienTichDat = item.dienTichDat;
                            checkbox.dataset.hangMuc = item.hangMuc;
                            checkbox.addEventListener('change', updateCostBasedOnSelection);
                            xayCell.appendChild(checkbox);
                        }
                    }
                    row.appendChild(xayCell);
                    
                    tableBody.appendChild(row);
                });
            }
            
            // Render the conditions met for additional floors
            function renderConditionsMet(dieuKien, coDieuKienCongTang) {
                const conditionsMet = document.getElementById('conditionsMet');
                const conditionsList = document.getElementById('conditionsList');
                
                // Clear previous content
                conditionsList.innerHTML = '';
                
                // Show/hide section based on whether there are conditions or not
                if (dieuKien.length > 0) {
                    conditionsMet.classList.remove('js-hidden');
                    
                    // Add each condition
                    dieuKien.forEach(condition => {
                        const conditionItem = document.createElement('div');
                        conditionItem.className = 'condition-item';
                        
                        const icon = document.createElement('i');
                        if (condition.met) {
                            icon.className = 'fas fa-check-circle condition-icon';
                        } else {
                            icon.className = 'fas fa-times-circle condition-icon not-met';
                        }
                        
                        const text = document.createElement('span');
                        text.textContent = condition.text;
                        if (!condition.met) {
                            text.style.color = 'var(--text-secondary)';
                        }
                        
                        conditionItem.appendChild(icon);
                        conditionItem.appendChild(text);
                        conditionsList.appendChild(conditionItem);
                    });
                    
                    // Add an explanation about the effect on height
                    const explanation = document.createElement('div');
                    explanation.className = 'mt-2 text-sm';
                    if (coDieuKienCongTang) {
                        explanation.innerHTML = '<i class="fas fa-info-circle text-blue-400 mr-1"></i> Đã đáp ứng điều kiện cộng tầng, chiều cao tại đỉnh mái đã được tăng theo quy định.';
                    } else {
                        explanation.innerHTML = '<i class="fas fa-info-circle text-blue-400 mr-1"></i> Chưa đáp ứng điều kiện cộng tầng nào, áp dụng chiều cao cơ bản.';
                        explanation.style.color = 'var(--text-secondary)';
                    }
                    conditionsList.appendChild(explanation);
                } else {
                    conditionsMet.classList.add('js-hidden');
                }
            }
            
            function updateCostBasedOnSelection() {
                // Lấy tất cả các checkbox đã chọn
                const checkedCheckboxes = document.querySelectorAll('.build-checkbox:checked');
                let tongDienTichXayDung = 0;
                let tongDienTichThietKe = 0;
                
                checkedCheckboxes.forEach(checkbox => {
                    const dienTichXD = parseFloat(checkbox.dataset.dienTichXD || 0);
                    const hangMuc = checkbox.dataset.hangMuc;
                    
                    // Tính tổng diện tích XD
                    tongDienTichXayDung += dienTichXD;
                    
                    // Tính tổng diện tích thiết kế (không bao gồm móng)
                    if (hangMuc !== 'Móng nhà') {
                        tongDienTichThietKe += dienTichXD;
                    }
                });
                
                // Thêm diện tích tầng đỉnh mái (luôn được tính)
                const tableRows = document.querySelectorAll('#khaiToanBody tr');
                tableRows.forEach(row => {
                    const cells = row.cells;
                    if (cells.length > 1 && cells[1].textContent === 'Tầng đỉnh mái') {
                        const dienTichXD = parseFloat(cells[4].textContent || 0);
                        tongDienTichXayDung += dienTichXD;
                        tongDienTichThietKe += dienTichXD;
                    }
                });
                
                // Cập nhật dòng tổng trong bảng
                const totalRows = document.querySelectorAll('.total-row');
                totalRows.forEach(row => {
                    const cells = row.cells;
                    if (cells.length > 4) {
                        cells[4].textContent = tongDienTichXayDung.toFixed(1);
                    }
                });
                
                // Lấy đơn giá từ form
                const donGiaThietKe = parseFormattedNumber(document.getElementById('donGiaThietKe').value) || 250000;
                const donGiaPhanTho = parseFormattedNumber(document.getElementById('donGiaPhanTho').value) || 4000000;
                const donGiaHoanThien = parseFormattedNumber(document.getElementById('donGiaHoanThien').value) || 2500000;
                const donGiaNoiThat = parseFormattedNumber(document.getElementById('donGiaNoiThat').value) || 2000000;
                
                // Tính chi phí
                const chiPhiThietKe = tongDienTichThietKe * donGiaThietKe;
                const chiPhiPhanTho = tongDienTichXayDung * donGiaPhanTho;
                const chiPhiHoanThien = tongDienTichXayDung * donGiaHoanThien;
                const chiPhiNoiThat = tongDienTichXayDung * 0.85 * donGiaNoiThat;
                
                const tongChiPhi = chiPhiThietKe + chiPhiPhanTho + chiPhiHoanThien + chiPhiNoiThat;
                
                // Hiển thị chi phí
                document.getElementById('chiPhiThietKe').textContent = formatCurrency(chiPhiThietKe);
                document.getElementById('chiPhiPhanTho').textContent = formatCurrency(chiPhiPhanTho);
                document.getElementById('chiPhiHoanThien').textContent = formatCurrency(chiPhiHoanThien);
                document.getElementById('chiPhiNoiThat').textContent = formatCurrency(chiPhiNoiThat);
                document.getElementById('tongChiPhi').textContent = formatCurrency(tongChiPhi);
            }
            
            // Handle calculate button click
            document.getElementById('tinhToanBtn').addEventListener('click', function() {
                // Show loading indicator
                const tinhToanText = document.getElementById('tinhToanText');
                const tinhToanLoader = document.getElementById('tinhToanLoader');
                tinhToanText.classList.add('hidden');
                tinhToanLoader.classList.remove('hidden');
                
                // Use setTimeout to allow UI to update before calculations
                setTimeout(() => {
                    try {
                        // Validate inputs
                        let isValid = true;
                        const dienTichDat = parseFloat(document.getElementById('dienTichDat').value);
                        const chieuSauDat = parseFloat(document.getElementById('chieuSauDat').value);
                        const chieuRongLoGioi = parseFloat(document.getElementById('chieuRongLoGioi').value);
                        const chieuRongMatTien = parseFloat(document.getElementById('chieuRongMatTien').value);
                        
                        // Check each required field
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
                        
                        // Get checkbox values
                        const quanTrungTam = document.getElementById('quanTrungTam').checked;
                        const trucDuongThuongMai = document.getElementById('trucDuongThuongMai').checked;
                        const matTienTren8m = document.getElementById('matTienTren8m').checked || chieuRongMatTien > 8.0;
                        const loDatGoc = document.getElementById('loDatGoc').checked;
                        
                        // Calculate values
                        const matDo = tinhMatDoXayDung(dienTichDat);
                        const dienTichXD = (dienTichDat * matDo / 100).toFixed(1);
                        const khoangLuiSauText = getKhoangLuiSauText(chieuSauDat);
                        const khoangLuiSau = tinhKhoangLuiSau(chieuSauDat);
                        const dienTichSanSau = (khoangLuiSau * chieuRongMatTien).toFixed(1);
                        const soTang = tinhSoTangToiDa(chieuRongLoGioi, quanTrungTam, trucDuongThuongMai, matTienTren8m);
                        
                        // Calculate height with the updated function
                        const chieuCao = tinhChieuCaoToiDa(chieuRongLoGioi, quanTrungTam, trucDuongThuongMai, matTienTren8m);
                        
                        const thongTinTangLung = xacDinhTangLung(chieuRongLoGioi);
                        const doVuonBanCongText = getDoVuonBanCongText(chieuRongLoGioi);
                        const dienTichBanCong = tinhDienTichBanCong(chieuRongLoGioi, chieuRongMatTien, soTang).toFixed(1);
                        
                        // Calculate khái toán
                        const khaiToan = tinhKhaiToanChiPhi(dienTichDat, soTang, matDo, chieuRongLoGioi, chieuRongMatTien, chieuSauDat);
                        
                        // Display results
                        document.getElementById('dienTichLoDat').textContent = dienTichDat.toFixed(1) + ' m²';
                        document.getElementById('dienTichXayDung').textContent = dienTichXD + ' m²';
                        document.getElementById('matDoXayDung').textContent = matDo + ' %';
                        document.getElementById('khoangLuiSau').textContent = khoangLuiSauText;
                        document.getElementById('dienTichSanSau').textContent = dienTichSanSau + ' m²';
                        document.getElementById('soTangToiDa').textContent = soTang + ' tầng';
                        document.getElementById('chieuCaoToiDaTaiCGXD').textContent = chieuCao.taiCGXD;
                        document.getElementById('chieuCaoToiDaTaiDinhMai').textContent = chieuCao.taiDinhMai;
                        
                        // Display conditions for additional floors
                        renderConditionsMet(chieuCao.dieuKien, chieuCao.coDieuKienCongTang);
                        
                        document.getElementById('thongTinTangLung').textContent = thongTinTangLung;
                        document.getElementById('doVuonBanCong').textContent = doVuonBanCongText;
                        document.getElementById('dienTichBanCong').textContent = dienTichBanCong + ' m²';
                        
                        // Display khái toán table
                        renderKhaiToanTable(khaiToan.khaiToanTable);
                        
                        // Calculate and display costs
                        const donGiaThietKe = parseFormattedNumber(document.getElementById('donGiaThietKe').value) || 250000;
                        const donGiaPhanTho = parseFormattedNumber(document.getElementById('donGiaPhanTho').value) || 4000000;
                        const donGiaHoanThien = parseFormattedNumber(document.getElementById('donGiaHoanThien').value) || 2500000;
                        const donGiaNoiThat = parseFormattedNumber(document.getElementById('donGiaNoiThat').value) || 2000000;
                        
                        const chiPhiThietKe = khaiToan.tongDienTichThietKe * donGiaThietKe;
                        const chiPhiPhanTho = khaiToan.tongDienTichXayDung * donGiaPhanTho;
                        const chiPhiHoanThien = khaiToan.tongDienTichXayDung * donGiaHoanThien;
                        const chiPhiNoiThat = khaiToan.tongDienTichXayDung * 0.85 * donGiaNoiThat;
                        
                        const tongChiPhi = chiPhiThietKe + chiPhiPhanTho + chiPhiHoanThien + chiPhiNoiThat;
                        
                        document.getElementById('chiPhiThietKe').textContent = formatCurrency(chiPhiThietKe);
                        document.getElementById('chiPhiPhanTho').textContent = formatCurrency(chiPhiPhanTho);
                        document.getElementById('chiPhiHoanThien').textContent = formatCurrency(chiPhiHoanThien);
                        document.getElementById('chiPhiNoiThat').textContent = formatCurrency(chiPhiNoiThat);
                        document.getElementById('tongChiPhi').textContent = formatCurrency(tongChiPhi);
                        
                        // Show success notification
                        showNotification('Tính toán thành công!', 'success');
                        
                        // Switch to results tab
                        document.querySelector('.nav-tab[data-tab="results-tab"]').click();
                    } catch (error) {
                        console.error('Calculation error:', error);
                        showNotification('Có lỗi xảy ra khi tính toán. Vui lòng thử lại.', 'error');
                    } finally {
                        // Hide loading indicator
                        tinhToanText.classList.remove('hidden');
                        tinhToanLoader.classList.add('hidden');
                    }
                }, 100);
            });
        });
    </script>
</body>
</html>

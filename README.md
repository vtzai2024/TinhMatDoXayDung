<html lang="vi">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
    <title>Tư vấn xây dựng theo QĐ 56-2021</title>
    <link href="https://cdn.jsdelivr.net/npm/tailwindcss@2.2.19/dist/tailwind.min.css" rel="stylesheet">
    <link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/@fortawesome/fontawesome-free@6.0.0/css/all.min.css">
    <style>
        :root {
            --primary: #3B82F6;
            --primary-dark: #2563EB;
            --green: #10B981;
            --green-dark: #059669;
            --bg-dark: #121212;
            --bg-card: #1E1E1E;
            --bg-input: #2D2D2D;
            --text-light: #E0E0E0;
            --text-secondary: #BBBBBB;
            --text-muted: #888888;
            --border-color: #333333;
            --error-color: #EF4444;
            --success-color: #10B981;
            --warning-color: #F59E0B;
        }
        
        html {
            scroll-behavior: smooth;
        }
        
        body {
            font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Open Sans', 'Helvetica Neue', sans-serif;
            background-color: var(--bg-dark);
            color: var(--text-light);
            line-height: 1.5;
            overflow-x: hidden;
        }
        
        /* Header Styles */
        .app-header {
            background-color: var(--bg-card);
            border-bottom: 1px solid var(--border-color);
        }
        
        /* Tabs Styles */
        .tab-container {
            background-color: var(--bg-card);
            border-top: 1px solid var(--border-color);
        }
        
        .tab-button {
            color: var(--text-secondary);
            transition: all 0.2s ease;
            font-size: 12px;
        }
        
        .tab-button.active {
            color: var(--primary);
        }
        
        .tab-content {
            display: none;
        }
        
        .tab-content.active {
            display: block;
            animation: fadeIn 0.3s ease-in-out;
        }
        
        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(10px); }
            to { opacity: 1; transform: translateY(0); }
        }
        
        /* Form Styles */
        .form-card {
            background-color: var(--bg-card);
            border: 1px solid var(--border-color);
            border-radius: 0.75rem;
        }
        
        .form-label {
            color: var(--text-light);
            font-weight: 500;
            margin-bottom: 0.5rem;
            display: block;
        }
        
        .form-input {
            background-color: var(--bg-input);
            border: 1px solid var(--border-color);
            color: var(--text-light);
            border-radius: 0.5rem;
            transition: all 0.2s;
            width: 100%;
            padding: 0.75rem;
            font-size: 16px;
        }
        
        .form-input:focus {
            border-color: var(--primary);
            outline: none;
            box-shadow: 0 0 0 3px rgba(59, 130, 246, 0.3);
        }
        
        .input-error {
            border-color: var(--error-color) !important;
        }
        
        .error-message {
            color: var(--error-color);
            font-size: 0.875rem;
            margin-top: 0.25rem;
            display: none;
        }
        
        .input-hint {
            color: var(--text-muted);
            font-size: 0.875rem;
            margin-top: 0.25rem;
        }
        
        /* Button Styles */
        .btn-primary {
            background-color: var(--primary);
            color: white;
            border-radius: 0.5rem;
            font-weight: 500;
            padding: 0.75rem 1.5rem;
            transition: all 0.2s ease;
            display: inline-flex;
            align-items: center;
            justify-content: center;
            min-height: 48px;
            font-size: 16px;
            width: 100%;
        }
        
        .btn-primary:hover, .btn-primary:focus {
            background-color: var(--primary-dark);
            transform: translateY(-1px);
        }
        
        .btn-primary:active {
            transform: translateY(1px);
        }
        
        /* Checkbox & Radio Styles */
        .custom-checkbox, .custom-radio {
            display: flex;
            align-items: center;
            margin-bottom: 0.75rem;
            cursor: pointer;
            user-select: none;
        }
        
        .custom-checkbox input[type="checkbox"],
        .custom-radio input[type="radio"] {
            accent-color: var(--primary);
            width: 20px;
            height: 20px;
            margin-right: 0.75rem;
        }
        
        /* Results Styles */
        .result-card {
            background-color: var(--bg-card);
            border: 1px solid var(--border-color);
            border-radius: 0.75rem;
        }
        
        .result-title {
            color: var(--primary);
            font-weight: 600;
            border-bottom: 1px solid var(--border-color);
            padding-bottom: 0.75rem;
            margin-bottom: 1rem;
        }
        
        .result-row {
            display: flex;
            justify-content: space-between;
            padding: 0.5rem 0;
            border-bottom: 1px dashed var(--border-color);
        }
        
        .result-label {
            color: var(--text-secondary);
            font-weight: 500;
        }
        
        .result-value {
            color: var(--primary);
            font-weight: 600;
        }
        
        /* Table Styles */
        .data-table {
            width: 100%;
            border-collapse: collapse;
        }
        
        .data-table th {
            background-color: var(--bg-input);
            color: var(--text-light);
            font-weight: 600;
            text-align: left;
            padding: 0.75rem;
            font-size: 14px;
        }
        
        .data-table td {
            padding: 0.75rem;
            border-bottom: 1px solid var(--border-color);
            color: var(--text-light);
            font-size: 14px;
        }
        
        .data-table tr:nth-child(even) {
            background-color: rgba(255, 255, 255, 0.05);
        }
        
        .total-row {
            background-color: var(--primary) !important;
            color: white !important;
            font-weight: 600;
        }
        
        .total-row td {
            color: white !important;
        }
        
        /* Table Checkboxes */
        .table-checkbox {
            width: 22px;
            height: 22px;
            accent-color: var(--primary);
        }
        
        .table-checkbox:disabled {
            opacity: 0.7;
        }
        
        /* Notifications */
        .notification {
            position: fixed;
            top: 20px;
            left: 50%;
            transform: translateX(-50%);
            padding: 15px 20px;
            border-radius: 8px;
            background-color: var(--bg-card);
            border-left: 4px solid var(--primary);
            box-shadow: 0 4px 12px rgba(0, 0, 0, 0.3);
            display: flex;
            align-items: center;
            z-index: 1000;
            max-width: 90%;
            animation: slideIn 0.3s ease-out, slideOut 0.3s ease-in 3s forwards;
            opacity: 0;
            visibility: hidden;
        }
        
        .notification.show {
            opacity: 1;
            visibility: visible;
        }
        
        .notification.error {
            border-left-color: var(--error-color);
        }
        
        .notification.success {
            border-left-color: var(--success-color);
        }
        
        .notification-icon {
            margin-right: 12px;
            font-size: 20px;
        }
        
        .notification-message {
            font-weight: 500;
        }
        
        @keyframes slideIn {
            from { opacity: 0; transform: translate(-50%, -20px); }
            to { opacity: 1; transform: translate(-50%, 0); }
        }
        
        @keyframes slideOut {
            from { opacity: 1; transform: translate(-50%, 0); }
            to { opacity: 0; transform: translate(-50%, -20px); visibility: hidden; }
        }
        
        /* Loader */
        .loader {
            display: inline-block;
            width: 24px;
            height: 24px;
            border: 3px solid rgba(255, 255, 255, 0.3);
            border-radius: 50%;
            border-top-color: white;
            animation: spin 1s ease-in-out infinite;
            margin-right: 10px;
        }
        
        @keyframes spin {
            to { transform: rotate(360deg); }
        }
        
        /* Mobile Bottom Navigation */
        .mobile-nav {
            position: fixed;
            bottom: 0;
            left: 0;
            right: 0;
            background-color: var(--bg-card);
            border-top: 1px solid var(--border-color);
            display: flex;
            justify-content: space-around;
            padding: 10px 0;
            z-index: 90;
        }
        
        .nav-item {
            display: flex;
            flex-direction: column;
            align-items: center;
            font-size: 12px;
            color: var(--text-secondary);
            padding: 8px 12px;
            border-radius: 8px;
            transition: all 0.2s;
        }
        
        .nav-item.active {
            color: var(--primary);
            background-color: rgba(59, 130, 246, 0.1);
        }
        
        .nav-item i {
            font-size: 20px;
            margin-bottom: 5px;
        }
        
        /* Back to top button */
        .back-to-top {
            position: fixed;
            bottom: 80px;
            right: 20px;
            background-color: var(--primary);
            color: white;
            width: 44px;
            height: 44px;
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            box-shadow: 0 4px 10px rgba(0, 0, 0, 0.3);
            z-index: 80;
            opacity: 0;
            visibility: hidden;
            transition: all 0.3s;
        }
        
        .back-to-top.visible {
            opacity: 1;
            visibility: visible;
        }
        
        /* Sticky Calculate Button */
        .sticky-calculate {
            position: fixed;
            bottom: 80px;
            left: 50%;
            transform: translateX(-50%);
            background-color: var(--primary);
            color: white;
            font-weight: 500;
            padding: 10px 25px;
            border-radius: 30px;
            box-shadow: 0 4px 10px rgba(0, 0, 0, 0.3);
            z-index: 80;
            display: flex;
            align-items: center;
            justify-content: center;
            min-width: 200px;
        }
        
        /* Logo */
        .logo-container {
            display: flex;
            align-items: center;
        }
        
        .logo-img {
            width: 32px;
            height: 32px;
            margin-right: 10px;
        }
        
        /* Container for app content */
        .app-container {
            padding-bottom: 70px; /* Space for bottom nav */
        }
        
        /* Section Block */
        .section-block {
            margin-bottom: 1.5rem;
            transition: all 0.3s;
        }
        
        .collapsible-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            cursor: pointer;
            padding: 0.75rem;
            background-color: var(--bg-input);
            border-radius: 0.5rem;
        }
        
        .collapsible-content {
            padding: 1rem 0;
            display: none;
        }
        
        .collapsible-content.show {
            display: block;
        }
        
        .toggle-icon {
            transition: transform 0.3s;
        }
        
        .toggle-icon.rotate {
            transform: rotate(180deg);
        }
        
        /* Utility Classes */
        .text-primary { color: var(--primary); }
        .text-green { color: var(--green); }
        .text-error { color: var(--error-color); }
        .text-warning { color: var(--warning-color); }
        .bg-primary { background-color: var(--primary); }
        .bg-card { background-color: var(--bg-card); }
        .p-safe { padding-bottom: calc(1rem + env(safe-area-inset-bottom)); }
    </style>
</head>
<body>
    <!-- Header -->
    <header class="app-header py-3 px-4 flex justify-between items-center">
        <a href="https://vtzspaxe.com/" target="_blank" class="logo-container">
            <img src="https://raw.githubusercontent.com/vtzai2024/TinhMatDoXayDung/main/LOGO%20VUONG%20NEN%20TRONG%20SUOT%20-chu%20trang-small.png" alt="Logo VTZ Spaxe" class="logo-img">
            <div>
                <div class="font-bold text-base text-primary">VTZ Spaxe</div>
                <div class="text-xs text-gray-400">Thiết kế & Xây dựng</div>
            </div>
        </a>
        <h1 class="text-lg font-bold ml-2 text-white">Tư vấn xây dựng</h1>
    </header>

    <!-- Main Content -->
    <div class="app-container pb-20">
        <!-- Tab Content Sections -->
        <div class="tab-content active" id="tab-input">
            <div class="p-4">
                <h2 class="text-lg font-bold mb-3">Thông tin lô đất</h2>
                <div class="form-card p-4 mb-5">
                    <div class="mb-4">
                        <label for="dienTichDat" class="form-label">Diện tích lô đất (m²)</label>
                        <input type="number" id="dienTichDat" class="form-input" placeholder="Nhập diện tích" min="0" step="0.01">
                        <div id="dienTichDat-error" class="error-message">Vui lòng nhập diện tích lô đất</div>
                    </div>
                    <div class="mb-4">
                        <label for="chieuSauDat" class="form-label">Chiều sâu lô đất (m)</label>
                        <input type="number" id="chieuSauDat" class="form-input" placeholder="Nhập chiều sâu" min="0" step="0.01">
                        <div id="chieuSauDat-error" class="error-message">Vui lòng nhập chiều sâu lô đất</div>
                    </div>
                    <div class="mb-4">
                        <label for="chieuRongLoGioi" class="form-label">Chiều rộng lộ giới (m)</label>
                        <input type="number" id="chieuRongLoGioi" class="form-input" placeholder="Nhập chiều rộng lộ giới" min="0" step="0.01">
                        <div id="chieuRongLoGioi-error" class="error-message">Vui lòng nhập chiều rộng lộ giới</div>
                    </div>
                    <div class="mb-4">
                        <label for="chieuRongMatTien" class="form-label">Chiều rộng mặt tiền (m)</label>
                        <input type="number" id="chieuRongMatTien" class="form-input" placeholder="Nhập chiều rộng mặt tiền" min="0" step="0.01">
                        <div id="chieuRongMatTien-error" class="error-message">Vui lòng nhập chiều rộng mặt tiền</div>
                    </div>
                </div>

                <h2 class="text-lg font-bold mb-3">Điều kiện đặc biệt</h2>
                <div class="form-card p-4 mb-5">
                    <label class="custom-checkbox">
                        <input type="checkbox" id="quanTrungTam" name="viTri">
                        <span>Thuộc Quận trung tâm hoặc Trung tâm cấp quận</span>
                    </label>
                    <label class="custom-checkbox">
                        <input type="checkbox" id="trucDuongThuongMai" name="viTri">
                        <span>Thuộc trục đường thương mại - dịch vụ</span>
                    </label>
                    <label class="custom-checkbox">
                        <input type="checkbox" id="matTienTren8m" name="viTri">
                        <span>Có chiều rộng mặt tiền > 8,0m</span>
                    </label>
                    <label class="custom-checkbox">
                        <input type="checkbox" id="loGoc" name="viTri">
                        <span>Lô góc tiếp giáp hai đường</span>
                    </label>
                </div>

                <h2 class="text-lg font-bold mb-3">Đơn giá thi công</h2>
                <div class="form-card p-4 mb-6">
                    <div class="mb-4">
                        <label for="donGiaThietKe" class="form-label">Đơn giá thiết kế (VNĐ/m²)</label>
                        <input type="text" id="donGiaThietKe" class="form-input" value="250000" inputmode="numeric">
                    </div>
                    <div class="mb-4">
                        <label for="donGiaPhanTho" class="form-label">Đơn giá phần thô (VNĐ/m²)</label>
                        <input type="text" id="donGiaPhanTho" class="form-input" value="4000000" inputmode="numeric">
                    </div>
                    <div class="mb-4">
                        <label for="donGiaHoanThien" class="form-label">Đơn giá hoàn thiện (VNĐ/m²)</label>
                        <input type="text" id="donGiaHoanThien" class="form-input" value="2500000" inputmode="numeric">
                    </div>
                    <div class="mb-4">
                        <label for="donGiaNoiThat" class="form-label">Đơn giá nội thất (VNĐ/m²)</label>
                        <input type="text" id="donGiaNoiThat" class="form-input" value="2000000" inputmode="numeric">
                    </div>
                </div>

                <h2 class="text-lg font-bold mb-3">Tùy chọn bổ sung</h2>
                <div class="form-card p-4 mb-6">
                    <label class="custom-checkbox">
                        <input type="checkbox" id="coTangLung" name="tangLung" checked>
                        <span>Có tầng lửng</span>
                    </label>
                    <div id="tangLungInfo" class="ml-8 text-sm text-gray-400 mb-3">Chỉ được phép khi chiều rộng lộ giới ≥ 6m</div>
                    
                    <label class="custom-checkbox">
                        <input type="checkbox" id="coTangDinhMai" name="tangDinhMai" checked disabled>
                        <span>Có tầng đỉnh mái</span>
                        <span class="ml-2 px-2 py-0.5 bg-blue-900 text-blue-300 text-xs rounded">Bắt buộc</span>
                    </label>
                    
                    <label class="custom-checkbox">
                        <input type="checkbox" id="coSanThuong" name="sanThuong" checked>
                        <span>Có sân thượng</span>
                    </label>
                    
                    <label class="custom-checkbox">
                        <input type="checkbox" id="coMaiBTCT" name="maiBTCT" checked>
                        <span>Có mái BTCT</span>
                    </label>
                </div>

                <!-- Calculate Button -->
                <button id="tinhToanBtn" class="btn-primary mb-10">
                    <i class="fas fa-calculator mr-2"></i>
                    <span>Tính toán</span>
                </button>
            </div>
        </div>

        <div class="tab-content" id="tab-results">
            <div class="p-4">
                <h2 class="text-lg font-bold mb-3">Kết quả tính toán</h2>
                
                <!-- Thông số cơ bản -->
                <div class="section-block">
                    <div class="collapsible-header">
                        <h3 class="font-semibold"><i class="fas fa-info-circle mr-2"></i> Thông số cơ bản</h3>
                        <i class="fas fa-chevron-down toggle-icon"></i>
                    </div>
                    <div class="collapsible-content show">
                        <div class="result-card p-4">
                            <div class="result-row">
                                <span class="result-label">Diện tích lô đất:</span>
                                <span class="result-value" id="dienTichLoDat">--</span>
                            </div>
                            <div class="result-row">
                                <span class="result-label">Diện tích được xây dựng:</span>
                                <span class="result-value" id="dienTichXayDung">--</span>
                            </div>
                            <div class="result-row">
                                <span class="result-label">Mật độ xây dựng:</span>
                                <span class="result-value" id="matDoXayDung">--</span>
                            </div>
                        </div>
                    </div>
                </div>
                
                <!-- Khoảng lùi -->
                <div class="section-block">
                    <div class="collapsible-header">
                        <h3 class="font-semibold"><i class="fas fa-arrows-alt-h mr-2"></i> Khoảng lùi</h3>
                        <i class="fas fa-chevron-down toggle-icon"></i>
                    </div>
                    <div class="collapsible-content">
                        <div class="result-card p-4">
                            <div class="result-row">
                                <span class="result-label">Khoảng lùi phía sau:</span>
                                <span class="result-value" id="khoangLuiSau">--</span>
                            </div>
                            <div class="result-row">
                                <span class="result-label">Diện tích sân sau:</span>
                                <span class="result-value" id="dienTichSanSau">--</span>
                            </div>
                        </div>
                    </div>
                </div>
                
                <!-- Chiều cao và số tầng -->
                <div class="section-block">
                    <div class="collapsible-header">
                        <h3 class="font-semibold"><i class="fas fa-building mr-2"></i> Chiều cao và số tầng</h3>
                        <i class="fas fa-chevron-down toggle-icon"></i>
                    </div>
                    <div class="collapsible-content">
                        <div class="result-card p-4">
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
                    </div>
                </div>
                
                <!-- Ban công và ô văng -->
                <div class="section-block">
                    <div class="collapsible-header">
                        <h3 class="font-semibold"><i class="fas fa-home mr-2"></i> Ban công và ô văng</h3>
                        <i class="fas fa-chevron-down toggle-icon"></i>
                    </div>
                    <div class="collapsible-content">
                        <div class="result-card p-4">
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
                </div>
                
                <!-- Điều kiện đặc biệt -->
                <div class="section-block" id="dieu-kien-dac-biet-section">
                    <div class="collapsible-header bg-yellow-800">
                        <h3 class="font-semibold"><i class="fas fa-exclamation-triangle mr-2 text-yellow-400"></i> Điều kiện đặc biệt</h3>
                        <i class="fas fa-chevron-down toggle-icon"></i>
                    </div>
                    <div class="collapsible-content">
                        <div class="p-4 bg-yellow-900 rounded-lg">
                            <p class="mb-2 text-yellow-200" id="dieu-kien-content">
                                Không có điều kiện đặc biệt áp dụng cho lô đất này.
                            </p>
                        </div>
                    </div>
                </div>
                
                <div class="p-4 bg-blue-900 border-l-4 border-blue-500 rounded-lg mt-4">
                    <div class="flex">
                        <div class="flex-shrink-0">
                            <i class="fas fa-info-circle text-blue-300"></i>
                        </div>
                        <div class="ml-3">
                            <h3 class="text-sm font-medium text-blue-300">Lưu ý:</h3>
                            <div class="mt-1 text-sm text-blue-200">
                                <p>Kết quả tính toán chỉ mang tính tham khảo theo QĐ số 56/2021/QĐ-UBND.</p>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>

        <div class="tab-content" id="tab-cost">
            <div class="p-4">
                <h2 class="text-lg font-bold mb-3">Khái toán chi phí xây dựng</h2>
                
                <div class="mb-4 overflow-x-auto">
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
                            <tr>
                                <td colspan="6" class="text-center py-4">
                                    Nhập thông tin và nhấn "Tính toán" để xem kết quả
                                </td>
                            </tr>
                        </tbody>
                    </table>
                </div>
                
                <div class="result-card p-4 mb-6">
                    <div class="section-block">
                        <div class="collapsible-header">
                            <h3 class="font-semibold"><i class="fas fa-money-bill-wave mr-2"></i> Chi tiết chi phí</h3>
                            <i class="fas fa-chevron-down toggle-icon"></i>
                        </div>
                        <div class="collapsible-content show">
                            <div class="mt-3">
                                <div class="flex justify-between items-center mb-3">
                                    <span class="font-medium">Chi phí thiết kế:</span>
                                    <span id="chiPhiThietKe" class="font-semibold text-primary">--</span>
                                </div>
                                <div class="flex justify-between items-center mb-3">
                                    <span class="font-medium">Chi phí phần thô:</span>
                                    <span id="chiPhiPhanTho" class="font-semibold text-primary">--</span>
                                </div>
                                <div class="flex justify-between items-center mb-3">
                                    <span class="font-medium">Chi phí hoàn thiện:</span>
                                    <span id="chiPhiHoanThien" class="font-semibold text-primary">--</span>
                                </div>
                                <div class="flex justify-between items-center mb-3">
                                    <span class="font-medium">Chi phí nội thất:</span>
                                    <span id="chiPhiNoiThat" class="font-semibold text-primary">--</span>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
                
                <div class="flex justify-between items-center p-4 bg-green-800 rounded-lg text-white mb-6">
                    <span class="font-bold text-lg">Tổng chi phí:</span>
                    <span id="tongChiPhi" class="font-bold text-lg">--</span>
                </div>
                
                <div class="text-sm text-gray-400">
                    <h3 class="font-medium mb-2">Ghi chú:</h3>
                    <ul class="list-disc pl-5 space-y-1">
                        <li>Chi phí thiết kế = Tổng diện tích thiết kế × Đơn giá thiết kế</li>
                        <li>Chi phí phần thô = Tổng diện tích xây dựng × Đơn giá phần thô</li>
                        <li>Chi phí hoàn thiện = Tổng diện tích xây dựng × Đơn giá hoàn thiện</li>
                        <li>Chi phí nội thất = Tổng diện tích xây dựng × 0,85 × Đơn giá nội thất</li>
                        <li>Chi phí chưa bao gồm thuế VAT và các chi phí phát sinh khác</li>
                    </ul>
                </div>
            </div>
        </div>

        <div class="tab-content" id="tab-info">
            <div class="p-4">
                <h2 class="text-lg font-bold mb-3">Thông tin phụ lục</h2>
                
                <!-- Lô đất đặc biệt -->
                <div class="section-block">
                    <div class="collapsible-header">
                        <h3 class="font-semibold"><i class="fas fa-map-marked-alt mr-2"></i> Lô đất đặc biệt</h3>
                        <i class="fas fa-chevron-down toggle-icon"></i>
                    </div>
                    <div class="collapsible-content">
                        <div class="mt-3 space-y-4">
                            <p>Lô đất có vị trí đặc biệt là lô đất có vị trí tại góc giao của hai hoặc ba đường (hoặc hẻm) hoặc tiếp giáp hai đường (hoặc hẻm) có quy định khác nhau về tầng cao.</p>
                            
                            <p class="font-medium text-primary">Nếu chiều rộng lô đất (tại vị trí tiếp giáp ranh lộ giới) tối thiểu 3,0m quay về phía đường lớn:</p>
                            <ul class="list-disc pl-5 space-y-1">
                                <li>Được phép xây dựng số tầng, chiều cao, ban công theo quy định của đường lớn.</li>
                                <li>Phần công trình tiếp giáp đường nhỏ được phép xây dựng số tầng, chiều cao, ban công theo quy định của đường lớn trong phạm vi 25m từ góc giao lộ.</li>
                            </ul>
                            
                            <p class="font-medium text-primary">Nếu chiều rộng lô đất nhỏ hơn 3,0m quay về phía đường lớn:</p>
                            <ul class="list-disc pl-5 space-y-1">
                                <li>Các chỉ tiêu quy hoạch kiến trúc được xác định theo quy định đối với đường nhỏ.</li>
                            </ul>
                        </div>
                    </div>
                </div>
                
                <!-- Lô đất dưới 36m² -->
                <div class="section-block">
                    <div class="collapsible-header">
                        <h3 class="font-semibold"><i class="fas fa-compress-arrows-alt mr-2"></i> Lô đất dưới 36m²</h3>
                        <i class="fas fa-chevron-down toggle-icon"></i>
                    </div>
                    <div class="collapsible-content">
                        <div class="mt-3 space-y-4">
                            <p>Các lô đất dự kiến xây dựng loại hình công trình nhà liên kế phải đảm bảo các điều kiện sau:</p>
                            
                            <p class="font-medium text-primary">Yêu cầu tối thiểu:</p>
                            <ul class="list-disc pl-5 space-y-1">
                                <li>Lô đất có quy mô diện tích phù hợp quy hoạch tối thiểu 36m²</li>
                                <li>Chiều rộng mặt tiền tại vị trí tiếp giáp lộ giới không nhỏ hơn 3,0m</li>
                                <li>Chiều sâu so với chỉ giới xây dựng không nhỏ hơn 3,0m</li>
                            </ul>
                            
                            <p class="font-medium text-primary">Đối với lô đất không đảm bảo yêu cầu:</p>
                            <ul class="list-disc pl-5 space-y-1">
                                <li>Chiều rộng mặt tiền/chiều sâu < 3,0m: Chỉ được cải tạo, sửa chữa theo hiện trạng hoặc xây mới với chiều cao tối đa tại CGXD 7,0m, tại đỉnh mái 9,0m</li>
                                <li>Diện tích < 15m² (chiều rộng/chiều sâu ≥ 3,0m): Chỉ được cải tạo, sửa chữa theo hiện trạng hoặc xây mới với chiều cao tại đỉnh mái không quá 7,0m</li>
                                <li>Diện tích 15-36m² (chiều rộng/chiều sâu ≥ 3,0m):
                                    <ul class="list-disc pl-5 space-y-1 mt-2">
                                        <li>Lộ giới ≥ 6m: Chiều cao tối đa tại CGXD 11,6m, tại đỉnh mái 13,6m</li>
                                        <li>Lộ giới < 6m: Chiều cao tối đa tại đỉnh mái 11,6m</li>
                                    </ul>
                                </li>
                            </ul>
                        </div>
                    </div>
                </div>
                
                <!-- Quy định chiều cao -->
                <div class="section-block">
                    <div class="collapsible-header">
                        <h3 class="font-semibold"><i class="fas fa-ruler-vertical mr-2"></i> Quy định chiều cao</h3>
                        <i class="fas fa-chevron-down toggle-icon"></i>
                    </div>
                    <div class="collapsible-content">
                        <div class="mt-3 overflow-x-auto">
                            <table class="data-table">
                                <tr>
                                    <th>Chiều rộng lộ giới</th>
                                    <th>Số tầng</th>
                                    <th>Chiều cao tại CGXD</th>
                                    <th>Chiều cao tại đỉnh mái</th>
                                </tr>
                                <tr>
                                    <td>L ≥ 25m</td>
                                    <td>6 tầng</td>
                                    <td>25,0m</td>
                                    <td>27,0m</td>
                                </tr>
                                <tr>
                                    <td>16m ≤ L < 25m</td>
                                    <td>5 tầng (+1)</td>
                                    <td>21,6m</td>
                                    <td>23,6m (27,0m)</td>
                                </tr>
                                <tr>
                                    <td>6m ≤ L < 16m</td>
                                    <td>4 tầng (+1)</td>
                                    <td>17,0m</td>
                                    <td>19,0m (22,4m)</td>
                                </tr>
                                <tr>
                                    <td>3,5m ≤ L < 6m</td>
                                    <td>3 tầng (+1)</td>
                                    <td>11,6m</td>
                                    <td>13,6m (15,6m)</td>
                                </tr>
                                <tr>
                                    <td>L < 3,5m</td>
                                    <td>3 tầng</td>
                                    <td>11,6m</td>
                                    <td>13,6m</td>
                                </tr>
                            </table>
                            <p class="mt-2 text-sm text-gray-400">(+1): Có thể cộng thêm 1 tầng nếu thuộc quận trung tâm, trục đường thương mại, hoặc mặt tiền > 8m</p>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>

    <!-- Mobile Nav -->
    <nav class="mobile-nav p-safe">
        <a class="nav-item active" data-tab="tab-input">
            <i class="fas fa-edit"></i>
            <span>Nhập liệu</span>
        </a>
        <a class="nav-item" data-tab="tab-results">
            <i class="fas fa-poll"></i>
            <span>Kết quả</span>
        </a>
        <a class="nav-item" data-tab="tab-cost">
            <i class="fas fa-calculator"></i>
            <span>Khái toán</span>
        </a>
        <a class="nav-item" data-tab="tab-info">
            <i class="fas fa-info-circle"></i>
            <span>Thông tin</span>
        </a>
    </nav>

    <!-- Sticky Calculate Button -->
    <button id="floatingCalcBtn" class="sticky-calculate hidden">
        <i class="fas fa-calculator mr-2"></i>
        <span>Tính toán</span>
    </button>

    <!-- Back to top button -->
    <button class="back-to-top" id="backToTop">
        <i class="fas fa-arrow-up"></i>
    </button>

    <!-- Notification Element -->
    <div id="notification" class="notification">
        <div class="notification-icon"><i class="fas fa-info-circle"></i></div>
        <div class="notification-message">Thông báo</div>
    </div>

    <!-- Footer -->
    <footer class="bg-gray-900 text-center py-4 text-sm text-gray-400 mt-4">
        <p class="mb-1">Ứng dụng được phát minh bởi công ty TNHH Thiết kế và xây dựng VTZ Spaxe</p>
        <p>© 2023-2025 VTZ Spaxe. Đã đăng ký bản quyền.</p>
    </footer>
    
    <script>
        document.addEventListener('DOMContentLoaded', function() {
            // Tab Navigation
            const tabButtons = document.querySelectorAll('.nav-item');
            const tabContents = document.querySelectorAll('.tab-content');
            
            function setActiveTab(tabId) {
                // Deactivate all tabs
                tabContents.forEach(content => {
                    content.classList.remove('active');
                });
                tabButtons.forEach(btn => {
                    btn.classList.remove('active');
                });
                
                // Activate selected tab
                document.getElementById(tabId).classList.add('active');
                document.querySelector(`[data-tab="${tabId}"]`).classList.add('active');
            }
            
            tabButtons.forEach(button => {
                button.addEventListener('click', function() {
                    const tabId = this.getAttribute('data-tab');
                    setActiveTab(tabId);
                    window.scrollTo(0, 0);
                });
            });
            
            // Collapsible sections
            const collapsibleHeaders = document.querySelectorAll('.collapsible-header');
            
            collapsibleHeaders.forEach(header => {
                header.addEventListener('click', function() {
                    // Toggle icon rotation
                    const toggleIcon = this.querySelector('.toggle-icon');
                    toggleIcon.classList.toggle('rotate');
                    
                    // Toggle content visibility
                    const content = this.nextElementSibling;
                    content.classList.toggle('show');
                });
            });
            
            // Back to top button
            const backToTopButton = document.getElementById('backToTop');
            
            window.addEventListener('scroll', function() {
                if (window.pageYOffset > 300) {
                    backToTopButton.classList.add('visible');
                } else {
                    backToTopButton.classList.remove('visible');
                }
            });
            
            backToTopButton.addEventListener('click', function() {
                window.scrollTo({
                    top: 0,
                    behavior: 'smooth'
                });
            });
            
            // Floating calculate button
            const floatingCalcBtn = document.getElementById('floatingCalcBtn');
            const mainCalcBtn = document.getElementById('tinhToanBtn');
            
            window.addEventListener('scroll', function() {
                // Show floating button when main button is out of view
                const mainBtnRect = mainCalcBtn.getBoundingClientRect();
                
                if (mainBtnRect.bottom < 0 && document.getElementById('tab-input').classList.contains('active')) {
                    floatingCalcBtn.classList.remove('hidden');
                } else {
                    floatingCalcBtn.classList.add('hidden');
                }
            });
            
            // Attach calculate event to floating button
            floatingCalcBtn.addEventListener('click', performCalculation);
            
            // Format currency inputs
            const currencyInputs = [
                document.getElementById('donGiaThietKe'),
                document.getElementById('donGiaPhanTho'),
                document.getElementById('donGiaHoanThien'),
                document.getElementById('donGiaNoiThat')
            ];
            
            currencyInputs.forEach(input => {
                input.addEventListener('blur', function() {
                    formatCurrencyInput(this);
                });
                
                input.addEventListener('focus', function() {
                    // Remove formatting when focused
                    this.value = this.value.replace(/\./g, '');
                });
                
                // Initialize with formatting
                formatCurrencyInput(input);
            });
            
            function formatCurrencyInput(input) {
                const value = input.value.replace(/\./g, '');
                if (value && !isNaN(parseFloat(value))) {
                    input.value = formatNumber(parseFloat(value));
                }
            }
            
            // Format number with thousands separator
            function formatNumber(number) {
                return number.toString().replace(/\B(?=(\d{3})+(?!\d))/g, ".");
            }
            
            // Format currency with VND
            function formatCurrency(number) {
                return formatNumber(Math.round(number)) + ' VNĐ';
            }
            
            // Parse formatted number back to numeric value
            function parseFormattedNumber(formattedNumber) {
                if (typeof formattedNumber === 'string') {
                    return parseInt(formattedNumber.replace(/\./g, ''));
                }
                return formattedNumber;
            }
            
            // Show notification
            function showNotification(message, type = 'info') {
                const notification = document.getElementById('notification');
                const notificationIcon = notification.querySelector('.notification-icon i');
                const notificationMessage = notification.querySelector('.notification-message');
                
                // Set icon based on type
                if (type === 'success') {
                    notificationIcon.className = 'fas fa-check-circle';
                    notification.className = 'notification success';
                } else if (type === 'error') {
                    notificationIcon.className = 'fas fa-exclamation-circle';
                    notification.className = 'notification error';
                } else {
                    notificationIcon.className = 'fas fa-info-circle';
                    notification.className = 'notification';
                }
                
                notificationMessage.textContent = message;
                notification.classList.add('show');
                
                // Hide notification after 3 seconds
                setTimeout(() => {
                    notification.classList.remove('show');
                }, 3000);
            }
            
            // Show input error
            function showInputError(inputId, message) {
                const input = document.getElementById(inputId);
                const errorElement = document.getElementById(`${inputId}-error`);
                
                if (input && errorElement) {
                    input.classList.add('input-error');
                    errorElement.textContent = message;
                    errorElement.style.display = 'block';
                }
            }
            
            // Hide input error
            function hideInputError(inputId) {
                const input = document.getElementById(inputId);
                const errorElement = document.getElementById(`${inputId}-error`);
                
                if (input && errorElement) {
                    input.classList.remove('input-error');
                    errorElement.style.display = 'none';
                }
            }
            
            // Validate inputs before calculation
            function validateInputs() {
                let isValid = true;
                
                // Required fields to validate
                const requiredFields = [
                    { id: 'dienTichDat', message: 'Vui lòng nhập diện tích lô đất' },
                    { id: 'chieuSauDat', message: 'Vui lòng nhập chiều sâu lô đất' },
                    { id: 'chieuRongLoGioi', message: 'Vui lòng nhập chiều rộng lộ giới' },
                    { id: 'chieuRongMatTien', message: 'Vui lòng nhập chiều rộng mặt tiền' }
                ];
                
                // Check each required field
                requiredFields.forEach(field => {
                    const input = document.getElementById(field.id);
                    const value = input.value.trim();
                    
                    if (!value || value === '0' || isNaN(parseFloat(value))) {
                        showInputError(field.id, field.message);
                        isValid = false;
                    } else {
                        hideInputError(field.id);
                    }
                });
                
                return isValid;
            }
            
            // Calculation functions
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
                    return 2; // 2 mét
                } else if (chieuSauDat >= 9) {
                    return 1; // 1 mét
                } else {
                    return 0.5; // Giả định 0.5m cho khoảng trống phía sau
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
            
            function tinhSoTangToiDa(chieuRongLoGioi, quanTrungTam, trucDuongThuongMai, matTienTren8m, dienTichDat, chieuRongMatTien, chieuSauDat) {
                // Kiểm tra trường hợp lô đất dưới 36m²
                if (dienTichDat < 36) {
                    if (chieuRongMatTien < 3.0 || chieuSauDat < 3.0) {
                        return 2; // Trường hợp đặc biệt cho lô đất không đủ điều kiện
                    } else if (dienTichDat < 15) {
                        return 2; // Lô đất < 15m² chỉ được xây max 2 tầng (chiều cao 7m)
                    } else if (dienTichDat >= 15 && dienTichDat < 36) {
                        if (chieuRongLoGioi >= 6) {
                            return 3; // Lô đất 15-36m² với lộ giới ≥ 6m
                        } else {
                            return 3; // Lô đất 15-36m² với lộ giới < 6m
                        }
                    }
                }
                
                // Trường hợp thông thường
                let soTangCoBan = 0;
                let soTangCongThem = 0;
                
                if (chieuRongLoGioi >= 25) {
                    soTangCoBan = 6;
                } else if (chieuRongLoGioi >= 16) {
                    soTangCoBan = 5;
                    // Xét điều kiện cộng thêm
                    if (quanTrungTam) soTangCongThem = Math.min(soTangCongThem + 1, 1);
                    if (trucDuongThuongMai) soTangCongThem = Math.min(soTangCongThem + 1, 1);
                    if (matTienTren8m) soTangCongThem = Math.min(soTangCongThem + 1, 1);
                } else if (chieuRongLoGioi >= 6) {
                    soTangCoBan = 4;
                    // Xét điều kiện cộng thêm
                    if (quanTrungTam) soTangCongThem = Math.min(soTangCongThem + 1, 1);
                    if (matTienTren8m) soTangCongThem = Math.min(soTangCongThem + 1, 1);
                } else if (chieuRongLoGioi >= 3.5) {
                    soTangCoBan = 3;
                    // Xét điều kiện cộng thêm
                    if (quanTrungTam) soTangCongThem = Math.min(soTangCongThem + 1, 1);
                    if (matTienTren8m) soTangCongThem = Math.min(soTangCongThem + 1, 1);
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
            
            function tinhChieuCaoToiDa(chieuRongLoGioi, soTang, dienTichDat, chieuRongMatTien, chieuSauDat) {
                let chieuCaoTaiCGXD = "";
                let chieuCaoTaiDinhMai = "";
                
                // Kiểm tra trường hợp lô đất dưới 36m²
                if (dienTichDat < 36) {
                    if (chieuRongMatTien < 3.0 || chieuSauDat < 3.0) {
                        // Lô đất có chiều rộng mặt tiền hoặc chiều sâu < 3.0m
                        chieuCaoTaiCGXD = "7,0m";
                        chieuCaoTaiDinhMai = "9,0m";
                        return { taiCGXD: chieuCaoTaiCGXD, taiDinhMai: chieuCaoTaiDinhMai };
                    } else if (dienTichDat < 15) {
                        // Lô đất < 15m² có chiều rộng/chiều sâu ≥ 3.0m
                        chieuCaoTaiCGXD = "5,0m";
                        chieuCaoTaiDinhMai = "7,0m";
                        return { taiCGXD: chieuCaoTaiCGXD, taiDinhMai: chieuCaoTaiDinhMai };
                    } else if (dienTichDat >= 15 && dienTichDat < 36) {
                        if (chieuRongLoGioi >= 6) {
                            // Lô đất 15-36m² với lộ giới ≥ 6m
                            chieuCaoTaiCGXD = "11,6m";
                            chieuCaoTaiDinhMai = "13,6m";
                            return { taiCGXD: chieuCaoTaiCGXD, taiDinhMai: chieuCaoTaiDinhMai };
                        } else {
                            // Lô đất 15-36m² với lộ giới < 6m
                            chieuCaoTaiCGXD = "9,6m";
                            chieuCaoTaiDinhMai = "11,6m";
                            return { taiCGXD: chieuCaoTaiCGXD, taiDinhMai: chieuCaoTaiDinhMai };
                        }
                    }
                }
                
                // Trường hợp thông thường
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
                    chieuCaoTaiCGXD = "9,6m";
                    chieuCaoTaiDinhMai = "11,6m";
                }
                
                return {
                    taiCGXD: chieuCaoTaiCGXD,
                    taiDinhMai: chieuCaoTaiDinhMai
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
            
            // Render the khái toán table
            function renderKhaiToanTable(khaiToanTable) {
                const tableBody = document.getElementById('khaiToanBody');
                tableBody.innerHTML = '';
                
                // Add rows to the table
                khaiToanTable.forEach((item, index) => {
                    const row = document.createElement('tr');
                    
                    // Set data attributes for row
                    row.dataset.dienTichDat = item.dienTichDat || 0;
                    row.dataset.heSo = item.heSo || 0;
                    row.dataset.dienTichXD = item.dienTichXD || 0;
                    
                    // Check if this is the total row
                    const isTotalRow = item.hangMuc.includes('Tổng');
                    
                    // Add class for total row
                    if (isTotalRow) {
                        row.classList.add('total-row');
                    }
                    
                    // Create STT cell
                    const sttCell = document.createElement('td');
                    sttCell.textContent = item.stt;
                    row.appendChild(sttCell);
                    
                    // Create Hạng mục cell
                    const hangMucCell = document.createElement('td');
                    hangMucCell.textContent = item.hangMuc;
                    row.appendChild(hangMucCell);
                    
                    // Create Diện tích cơ sở cell
                    const dienTichDatCell = document.createElement('td');
                    dienTichDatCell.textContent = item.dienTichDat ? item.dienTichDat.toFixed(1) : '';
                    row.appendChild(dienTichDatCell);
                    
                    // Create Hệ số cell
                    const heSoCell = document.createElement('td');
                    heSoCell.textContent = item.heSo ? item.heSo : '';
                    row.appendChild(heSoCell);
                    
                    // Create Diện tích XD cell
                    const dienTichXDCell = document.createElement('td');
                    dienTichXDCell.textContent = item.dienTichXD ? item.dienTichXD.toFixed(1) : '';
                    row.appendChild(dienTichXDCell);
                    
                    // Create Xây dựng cell with checkbox
                    const xayDungCell = document.createElement('td');
                    if (!isTotalRow) {
                        const checkbox = document.createElement('input');
                        checkbox.type = 'checkbox';
                        checkbox.checked = true;
                        checkbox.classList.add('table-checkbox', 'build-checkbox');
                        checkbox.addEventListener('change', updateCostBasedOnSelection);
                        
                        // If this is the "Tầng đỉnh mái" row, make it mandatory
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
            }
            
            // Update cost calculation based on checkbox selection
            function updateCostBasedOnSelection() {
                const buildCheckboxes = document.querySelectorAll('.build-checkbox');
                let tongDienTichThietKe = 0;
                let tongDienTichXayDung = 0;
                
                buildCheckboxes.forEach(checkbox => {
                    if (checkbox.checked) {
                        const row = checkbox.closest('tr');
                        const dienTichXD = parseFloat(row.dataset.dienTichXD || 0);
                        const heSo = parseFloat(row.dataset.heSo || 0);
                        const dienTichDat = parseFloat(row.dataset.dienTichDat || 0);
                        
                        tongDienTichXayDung += dienTichXD;
                        
                        // Only include in design area if not "Móng nhà"
                        const hangMuc = row.cells[1].textContent;
                        if (hangMuc !== 'Móng nhà' && heSo > 0 && dienTichDat > 0) {
                            tongDienTichThietKe += dienTichXD;
                        }
                    }
                });
                
                // Get unit prices
                const donGiaThietKe = parseFormattedNumber(document.getElementById('donGiaThietKe').value) || 250000;
                const donGiaPhanTho = parseFormattedNumber(document.getElementById('donGiaPhanTho').value) || 4000000;
                const donGiaHoanThien = parseFormattedNumber(document.getElementById('donGiaHoanThien').value) || 2500000;
                const donGiaNoiThat = parseFormattedNumber(document.getElementById('donGiaNoiThat').value) || 2000000;
                
                // Calculate costs
                const chiPhiThietKe = tongDienTichThietKe * donGiaThietKe;
                const chiPhiPhanTho = tongDienTichXayDung * donGiaPhanTho;
                const chiPhiHoanThien = tongDienTichXayDung * donGiaHoanThien;
                const chiPhiNoiThat = tongDienTichXayDung * 0.85 * donGiaNoiThat;
                
                const tongChiPhi = chiPhiThietKe + chiPhiPhanTho + chiPhiHoanThien + chiPhiNoiThat;
                
                // Calculate percentages
                const percentThietKe = ((chiPhiThietKe / tongChiPhi) * 100).toFixed(1);
                const percentPhanTho = ((chiPhiPhanTho / tongChiPhi) * 100).toFixed(1);
                const percentHoanThien = ((chiPhiHoanThien / tongChiPhi) * 100).toFixed(1);
                const percentNoiThat = ((chiPhiNoiThat / tongChiPhi) * 100).toFixed(1);
                
                // Update the displayed costs
                document.getElementById('chiPhiThietKe').innerHTML = `${formatCurrency(chiPhiThietKe)} <span class="text-sm text-gray-400">${percentThietKe}%</span>`;
                document.getElementById('chiPhiPhanTho').innerHTML = `${formatCurrency(chiPhiPhanTho)} <span class="text-sm text-gray-400">${percentPhanTho}%</span>`;
                document.getElementById('chiPhiHoanThien').innerHTML = `${formatCurrency(chiPhiHoanThien)} <span class="text-sm text-gray-400">${percentHoanThien}%</span>`;
                document.getElementById('chiPhiNoiThat').innerHTML = `${formatCurrency(chiPhiNoiThat)} <span class="text-sm text-gray-400">${percentNoiThat}%</span>`;
                document.getElementById('tongChiPhi').textContent = formatCurrency(tongChiPhi);
                
                // Update the total row in the khái toán table
                const totalCell = document.querySelector('.total-row td:nth-child(5)');
                if (totalCell) {
                    totalCell.textContent = tongDienTichXayDung.toFixed(1);
                }
            }
            
            function tinhKhaiToanChiPhi(dienTichDat, soTang, matDoXayDung, chieuRongLoGioi, chieuRongMatTien, chieuSauDat) {
                // Lấy trạng thái checkbox từ giao diện
                const coTangLung = document.getElementById('coTangLung').checked && !document.getElementById('coTangLung').disabled;
                const coTangDinhMai = document.getElementById('coTangDinhMai').checked;
                const coSanThuong = document.getElementById('coSanThuong').checked;
                
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
                const heSoMong = 0.5; // Sử dụng hệ số móng mặc định
                khaiToanTable.push({
                    stt: stt++,
                    hangMuc: 'Móng nhà',
                    dienTichDat: dienTichXDMax,
                    heSo: heSoMong,
                    dienTichXD: dienTichXDMax * heSoMong
                });
                // Không cộng vào tongDienTichThietKe như yêu cầu
                tongDienTichXayDung += dienTichXDMax * heSoMong;
                
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
                    stt: stt,
                    hangMuc: 'Tổng diện tích',
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
            
            // Check and update tầng lửng availability
            function updateTangLungAvailability(chieuRongLoGioi) {
                const tangLungCheckbox = document.getElementById('coTangLung');
                const tangLungInfo = document.getElementById('tangLungInfo');
                
                if (chieuRongLoGioi < 6) {
                    // Nếu chiều rộng lộ giới < 6m, không được phép có tầng lửng
                    tangLungCheckbox.checked = false;
                    tangLungCheckbox.disabled = true;
                    tangLungInfo.classList.add('text-red-500');
                    tangLungInfo.classList.remove('text-gray-400');
                } else {
                    // Nếu chiều rộng lộ giới ≥ 6m, được phép có tầng lửng
                    tangLungCheckbox.disabled = false;
                    tangLungInfo.classList.remove('text-red-500');
                    tangLungInfo.classList.add('text-gray-400');
                }
            }
            
            // Check for special conditions (lô đất dưới 36m² or lô góc)
            function checkSpecialConditions(dienTichDat, chieuRongMatTien, chieuSauDat, loGoc) {
                const dieuKienSection = document.getElementById('dieu-kien-dac-biet-section');
                const dieuKienContent = document.getElementById('dieu-kien-content');
                
                if (dienTichDat < 36) {
                    dieuKienSection.querySelector('.collapsible-header').classList.add('bg-yellow-800');
                    
                    // Check specific case
                    if (chieuRongMatTien < 3.0 || chieuSauDat < 3.0) {
                        dieuKienContent.innerHTML = 
                            `<strong class="text-white">Lô đất không đủ điều kiện xây dựng nhà liên kế!</strong><br>
                            Lô đất có chiều rộng mặt tiền hoặc chiều sâu < 3,0m chỉ được cải tạo, sửa chữa theo quy mô hiện trạng
                            hoặc xây dựng mới với chiều cao tối đa tại CGXD 7,0m và tại đỉnh mái không quá 9,0m.`;
                    } else if (dienTichDat < 15) {
                        dieuKienContent.innerHTML = 
                            `<strong class="text-white">Lô đất có diện tích < 15m²:</strong><br>
                            Chỉ được cải tạo, sửa chữa theo hiện trạng hoặc xây dựng mới với chiều cao tối đa tại đỉnh mái không quá 7,0m.`;
                    } else {
                        // 15-36m²
                        if (chieuRongMatTien >= 3.0 && chieuSauDat >= 3.0) {
                            if (chieuRongLoGioi >= 6) {
                                dieuKienContent.innerHTML = 
                                    `<strong class="text-white">Lô đất có diện tích từ 15m² đến dưới 36m²:</strong><br>
                                    Tiếp giáp đường có lộ giới ≥ 6m: chiều cao tối đa tại CGXD không quá 11,6m và 
                                    chiều cao tối đa tại đỉnh mái không quá 13,6m.`;
                            } else {
                                dieuKienContent.innerHTML = 
                                    `<strong class="text-white">Lô đất có diện tích từ 15m² đến dưới 36m²:</strong><br>
                                    Tiếp giáp đường có lộ giới < 6m: chiều cao tối đa tại đỉnh mái không quá 11,6m.`;
                            }
                        }
                    }
                    
                    // Show special condition section
                    dieuKienSection.style.display = 'block';
                    // Expand the section
                    if (!dieuKienSection.querySelector('.collapsible-content').classList.contains('show')) {
                        dieuKienSection.querySelector('.collapsible-header').click();
                    }
                } else if (loGoc) {
                    dieuKienSection.querySelector('.collapsible-header').classList.add('bg-blue-900');
                    dieuKienContent.innerHTML = 
                        `<strong class="text-white">Lô đất góc tiếp giáp hai đường:</strong><br>
                        Nếu chiều rộng lô đất (tại vị trí tiếp giáp ranh lộ giới) tối thiểu 3,0m quay về phía đường lớn, 
                        được phép xây dựng số tầng, chiều cao, ban công theo quy định của đường lớn. 
                        Phần tiếp giáp đường nhỏ được áp dụng quy định của đường lớn trong phạm vi 25m từ góc giao lộ.`;
                    
                    // Show special condition section
                    dieuKienSection.style.display = 'block';
                    // Expand the section
                    if (!dieuKienSection.querySelector('.collapsible-content').classList.contains('show')) {
                        dieuKienSection.querySelector('.collapsible-header').click();
                    }
                } else {
                    // Hide special condition section if no special conditions apply
                    dieuKienSection.style.display = 'none';
                }
            }
            
            // Main calculation function
            function performCalculation() {
                // Show loading in button
                const calcBtn = document.getElementById('tinhToanBtn');
                const originalBtnText = calcBtn.innerHTML;
                calcBtn.innerHTML = '<div class="loader"></div> Đang tính...';
                calcBtn.disabled = true;
                
                // Validate inputs
                if (!validateInputs()) {
                    calcBtn.innerHTML = originalBtnText;
                    calcBtn.disabled = false;
                    showNotification('Vui lòng nhập đầy đủ thông tin lô đất', 'error');
                    return;
                }
                
                // Delay calculation slightly to show loading effect
                setTimeout(() => {
                    try {
                        // Get input values
                        const dienTichDat = parseFloat(document.getElementById('dienTichDat').value);
                        const chieuSauDat = parseFloat(document.getElementById('chieuSauDat').value);
                        const chieuRongLoGioi = parseFloat(document.getElementById('chieuRongLoGioi').value);
                        const chieuRongMatTien = parseFloat(document.getElementById('chieuRongMatTien').value);
                        
                        // Get checkbox values
                        const quanTrungTam = document.getElementById('quanTrungTam').checked;
                        const trucDuongThuongMai = document.getElementById('trucDuongThuongMai').checked;
                        const matTienTren8m = document.getElementById('matTienTren8m').checked || chieuRongMatTien > 8.0;
                        const loGoc = document.getElementById('loGoc').checked;
                        
                        // Update tầng lửng availability
                        updateTangLungAvailability(chieuRongLoGioi);
                        
                        // Check for special conditions (lô đất < 36m² or lô góc)
                        checkSpecialConditions(dienTichDat, chieuRongMatTien, chieuSauDat, loGoc);
                        
                        // Calculate mật độ xây dựng
                        const matDo = tinhMatDoXayDung(dienTichDat);
                        
                        // Calculate diện tích được xây dựng
                        const dienTichXD = (dienTichDat * matDo / 100).toFixed(1);
                        
                        // Calculate khoảng lùi phía sau
                        const khoangLuiSauText = getKhoangLuiSauText(chieuSauDat);
                        
                        // Calculate diện tích sân sau
                        const khoangLuiSau = tinhKhoangLuiSau(chieuSauDat);
                        const dienTichSanSau = (khoangLuiSau * chieuRongMatTien).toFixed(1);
                        
                        // Calculate số tầng tối đa
                        const soTang = tinhSoTangToiDa(chieuRongLoGioi, quanTrungTam, trucDuongThuongMai, matTienTren8m, dienTichDat, chieuRongMatTien, chieuSauDat);
                        
                        // Calculate chiều cao tối đa
                        const chieuCao = tinhChieuCaoToiDa(chieuRongLoGioi, soTang, dienTichDat, chieuRongMatTien, chieuSauDat);
                        
                        // Get thông tin tầng lửng
                        const thongTinTangLung = xacDinhTangLung(chieuRongLoGioi);
                        
                        // Calculate ban công
                        const doVuonBanCongText = getDoVuonBanCongText(chieuRongLoGioi);
                        const dienTichBanCong = tinhDienTichBanCong(chieuRongLoGioi, chieuRongMatTien, soTang).toFixed(1);
                        
                        // Calculate khái toán chi phí
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
                        document.getElementById('thongTinTangLung').textContent = thongTinTangLung;
                        document.getElementById('doVuonBanCong').textContent = doVuonBanCongText;
                        document.getElementById('dienTichBanCong').textContent = dienTichBanCong + ' m²';
                        
                        // Display khái toán table
                        renderKhaiToanTable(khaiToan.khaiToanTable);
                        
                        // Calculate and display costs
                        updateCostBasedOnSelection();
                        
                        // Switch to results tab
                        setActiveTab('tab-results');
                        
                        // Show success notification
                        showNotification('Tính toán thành công!', 'success');
                    } catch (error) {
                        console.error('Calculation error:', error);
                        showNotification('Có lỗi xảy ra trong quá trình tính toán. Vui lòng thử lại!', 'error');
                    } finally {
                        // Reset button state
                        calcBtn.innerHTML = originalBtnText;
                        calcBtn.disabled = false;
                    }
                }, 500); // Short delay for loading effect
            }
            
            // Attach calculate event to main button
            document.getElementById('tinhToanBtn').addEventListener('click', performCalculation);
            
            // Update mặt tiền > 8m checkbox when changing chiều rộng mặt tiền
            document.getElementById('chieuRongMatTien').addEventListener('input', function() {
                const chieuRongMatTien = parseFloat(this.value) || 0;
                document.getElementById('matTienTren8m').checked = chieuRongMatTien > 8.0;
            });
            
            // Update tầng lửng when changing chiều rộng lộ giới
            document.getElementById('chieuRongLoGioi').addEventListener('input', function() {
                const chieuRongLoGioi = parseFloat(this.value) || 0;
                updateTangLungAvailability(chieuRongLoGioi);
            });
        });
    </script>
</body>
</html>

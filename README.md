<html lang="vi">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Máy tính Quy định xây dựng TP. HCM</title>
    <link href="https://cdn.jsdelivr.net/npm/tailwindcss@2.2.19/dist/tailwind.min.css" rel="stylesheet">
    <link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/@fortawesome/fontawesome-free@6.0.0/css/all.min.css">
    <style>
        :root {
            --primary: #3B82F6;
            --primary-dark: #2563EB;
            --primary-light: #60a5fa;
            --green: #10B981;
            --green-dark: #059669;
            --background: #121212;
            --background-alt: #1e1e1e;
            --background-card: #1d1d1d;
            --text-primary: #e0e0e0;
            --text-secondary: #a0a0a0;
            --text-muted: #6c7280;
            --border-color: #2a2a2a;
            --highlight: #2d2d2d;
            --highlight-hover: #363636;
            --accent-yellow: #fbbf24;
            --accent-red: #ef4444;
            --accent-blue: #1e40af;
        }
        
        body {
            font-family: 'Segoe UI', Arial, sans-serif;
            background-color: var(--background);
            color: var(--text-primary);
            -webkit-tap-highlight-color: transparent;
        }
        
        /* Mobile sidebar */
        .mobile-sidebar {
            width: 85%;
            max-width: 280px;
            z-index: 1000;
            transition: transform 0.3s ease;
            transform: translateX(-105%);
            position: fixed;
            top: 0;
            left: 0;
            height: 100vh;
            background-color: var(--background-alt);
            border-right: 1px solid var(--border-color);
            overflow-y: auto;
        }
        
        .mobile-sidebar.open {
            transform: translateX(0);
            box-shadow: 0 0 15px rgba(0, 0, 0, 0.5);
        }
        
        .overlay {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background-color: rgba(0, 0, 0, 0.7);
            opacity: 0;
            visibility: hidden;
            transition: all 0.3s ease;
            z-index: 999;
        }
        
        .overlay.active {
            opacity: 1;
            visibility: visible;
        }
        
        .mobile-header {
            position: sticky;
            top: 0;
            z-index: 100;
            background-color: var(--background-alt);
            box-shadow: 0 1px 3px rgba(0, 0, 0, 0.3);
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 0.75rem 1rem;
        }
        
        .nav-item {
            color: var(--text-secondary);
            border-left: 3px solid transparent;
            transition: all 0.2s ease;
        }
        
        .nav-item:hover {
            background-color: var(--highlight-hover);
            color: var(--primary-light);
            border-left-color: var(--primary);
        }
        
        .nav-item.active {
            background-color: var(--highlight);
            color: var(--primary-light);
            border-left-color: var(--primary);
            font-weight: 500;
        }
        
        .card {
            background-color: var(--background-card);
            border: 1px solid var(--border-color);
            border-radius: 0.5rem;
            box-shadow: 0 1px 3px rgba(0, 0, 0, 0.3);
            margin-bottom: 1rem;
        }
        
        .card-header {
            border-bottom: 1px solid var(--border-color);
            color: var(--text-primary);
        }
        
        .btn-primary {
            background-color: var(--primary);
            color: white;
            transition: all 0.2s ease;
        }
        
        .btn-primary:hover {
            background-color: var(--primary-dark);
            transform: translateY(-1px);
        }
        
        .btn-primary:active {
            transform: translateY(0);
        }
        
        .checkbox-item input[type="checkbox"] {
            accent-color: var(--primary);
            width: 18px;
            height: 18px;
        }
        
        .radio-item input[type="radio"] {
            accent-color: var(--primary);
            width: 18px;
            height: 18px;
        }
        
        .form-input {
            background-color: var(--background-alt);
            border: 1px solid var(--border-color);
            border-radius: 0.375rem;
            padding: 0.75rem;
            width: 100%;
            color: var(--text-primary);
            font-size: 16px;
        }
        
        .form-input:focus {
            outline: none;
            border-color: var(--primary);
            box-shadow: 0 0 0 3px rgba(59, 130, 246, 0.3);
        }
        
        .form-label {
            color: var(--text-primary);
            font-weight: 500;
            margin-bottom: 0.5rem;
            display: block;
        }
        
        .input-hint {
            color: var(--text-secondary);
            font-size: 0.75rem;
            margin-top: 0.25rem;
        }
        
        .tab-container {
            display: flex;
            overflow-x: auto;
            border-bottom: 1px solid var(--border-color);
            margin-bottom: 1rem;
            scrollbar-width: none;
            -ms-overflow-style: none;
        }
        
        .tab-container::-webkit-scrollbar {
            display: none;
        }
        
        .tab-button {
            color: var(--text-secondary);
            padding: 0.75rem 1rem;
            white-space: nowrap;
            border-bottom: 2px solid transparent;
            transition: all 0.2s ease;
        }
        
        .tab-button:hover {
            color: var(--primary-light);
        }
        
        .tab-button.active {
            color: var(--primary-light);
            border-bottom-color: var(--primary);
        }
        
        .tab-content {
            display: none;
        }
        
        .tab-content.active {
            display: block;
        }
        
        .result-section {
            margin-bottom: 1rem;
        }
        
        .result-title {
            color: var(--primary-light);
            font-weight: 600;
            border-bottom: 1px solid var(--border-color);
            padding-bottom: 0.5rem;
            margin-bottom: 0.5rem;
            font-size: 0.9rem;
        }
        
        .result-row {
            display: flex;
            justify-content: space-between;
            margin-bottom: 0.5rem;
            padding-bottom: 0.5rem;
            border-bottom: 1px dashed var(--border-color);
            flex-wrap: wrap;
        }
        
        .result-label {
            color: var(--text-secondary);
            font-weight: 500;
            font-size: 0.85rem;
        }
        
        .result-value {
            color: var(--primary-light);
            font-weight: 600;
            font-size: 0.85rem;
        }
        
        .khai-toan-table {
            width: 100%;
            border-collapse: collapse;
            font-size: 0.8rem;
        }
        
        .khai-toan-table th {
            background-color: var(--highlight);
            color: var(--text-primary);
            font-weight: 600;
            text-align: left;
            padding: 0.5rem 0.4rem;
            border: 1px solid var(--border-color);
        }
        
        .khai-toan-table td {
            padding: 0.5rem 0.4rem;
            border: 1px solid var(--border-color);
            color: var(--text-primary);
        }
        
        .khai-toan-table tr:nth-child(even) {
            background-color: var(--highlight);
        }
        
        .total-row {
            background-color: var(--primary-dark) !important;
            color: white !important;
            font-weight: 600;
        }
        
        .total-row td {
            color: white !important;
        }
        
        .notification {
            position: fixed;
            top: 20px;
            right: 20px;
            padding: 12px 20px;
            background-color: var(--background-card);
            border-left: 4px solid var(--primary);
            box-shadow: 0 2px 8px rgba(0, 0, 0, 0.4);
            border-radius: 4px;
            display: flex;
            align-items: center;
            transform: translateX(120%);
            transition: transform 0.3s ease;
            z-index: 1000;
            color: var(--text-primary);
        }
        
        .notification.show {
            transform: translateX(0);
        }
        
        .notification.error {
            border-left-color: var(--accent-red);
        }
        
        .notification.success {
            border-left-color: var(--green);
        }
        
        .error-message {
            color: var(--accent-red);
            font-size: 0.75rem;
            margin-top: 0.25rem;
            display: none;
        }
        
        .percent-badge {
            display: inline-block;
            background-color: var(--highlight);
            color: var(--text-primary);
            padding: 0.1rem 0.3rem;
            border-radius: 0.25rem;
            font-size: 0.7rem;
            margin-left: 0.3rem;
            font-weight: 500;
        }
        
        .construction-area-section {
            margin-bottom: 1rem;
            border-bottom: 1px solid var(--border-color);
            padding-bottom: 1rem;
        }
        
        .construction-area-title {
            font-weight: 600;
            color: var(--primary-light);
            margin-bottom: 0.5rem;
            font-size: 0.9rem;
        }
        
        .construction-area-grid {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 0.5rem;
        }
        
        .construction-radio-item {
            display: flex;
            align-items: center;
            margin-bottom: 0.5rem;
        }
        
        .construction-radio-item input[type="radio"] {
            accent-color: var(--primary);
            margin-right: 0.5rem;
        }
        
        .radio-label {
            display: flex;
            justify-content: space-between;
            width: 100%;
            font-size: 0.8rem;
        }
        
        .radio-coefficient {
            color: var(--primary-light);
            font-weight: 500;
            font-size: 0.75rem;
        }
        
        .fab {
            position: fixed;
            bottom: 20px;
            right: 20px;
            width: 56px;
            height: 56px;
            border-radius: 50%;
            background-color: var(--primary);
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.4);
            display: flex;
            justify-content: center;
            align-items: center;
            color: white;
            z-index: 50;
            transition: all 0.3s ease;
        }
        
        .fab:active {
            transform: scale(0.95);
        }
        
        .back-to-top {
            position: fixed;
            bottom: 90px;
            right: 20px;
            width: 40px;
            height: 40px;
            border-radius: 50%;
            background-color: var(--background-card);
            box-shadow: 0 2px 5px rgba(0, 0, 0, 0.4);
            display: flex;
            justify-content: center;
            align-items: center;
            color: var(--primary-light);
            z-index: 50;
            transition: all 0.3s ease;
            opacity: 0;
            visibility: hidden;
        }
        
        .back-to-top.show {
            opacity: 1;
            visibility: visible;
        }
        
        .alert-yellow {
            background-color: rgba(251, 191, 36, 0.1);
            border-left-color: var(--accent-yellow);
        }
        
        .alert-red {
            background-color: rgba(239, 68, 68, 0.1);
            border-left-color: var(--accent-red);
        }
        
        .text-yellow-dark {
            color: var(--accent-yellow);
        }
        
        .text-red-dark {
            color: var(--accent-red);
        }
        
        .info-badge {
            background-color: rgba(59, 130, 246, 0.2);
            color: var(--primary-light);
        }
        
        .bottom-nav {
            position: fixed;
            bottom: 0;
            left: 0;
            width: 100%;
            background-color: var(--background-alt);
            display: flex;
            justify-content: space-around;
            padding: 0.5rem 0;
            border-top: 1px solid var(--border-color);
            z-index: 40;
        }
        
        .bottom-nav-item {
            display: flex;
            flex-direction: column;
            align-items: center;
            padding: 0.5rem;
            color: var(--text-secondary);
            font-size: 0.7rem;
        }
        
        .bottom-nav-item.active {
            color: var(--primary-light);
        }
        
        .bottom-nav-item i {
            font-size: 1.1rem;
            margin-bottom: 0.2rem;
        }
        
        .collapsible-section {
            margin-bottom: 0.75rem;
        }
        
        .collapsible-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 0.75rem;
            background-color: var(--highlight);
            border-radius: 0.375rem;
            cursor: pointer;
            user-select: none;
        }
        
        .collapsible-content {
            padding: 0 0.5rem;
            max-height: 0;
            overflow: hidden;
            transition: max-height 0.3s ease;
        }
        
        .collapsible-content.expanded {
            max-height: 1000px;
            padding: 0.75rem 0.5rem;
        }
        
        /* Styles cho lô đất < 36m² */
        .small-lot-warning {
            background-color: rgba(239, 68, 68, 0.1);
            border-left: 4px solid var(--accent-red);
            padding: 0.75rem;
            margin-top: 0.75rem;
            border-radius: 0.25rem;
        }
    </style>
</head>
<body class="pb-16">
    <!-- Mobile Header -->
    <header class="mobile-header">
        <button id="menuToggle" class="p-2">
            <i class="fas fa-bars text-xl text-gray-300"></i>
        </button>
        <div class="text-center">
            <div class="font-bold text-primary-light">Quy định xây dựng TP.HCM</div>
        </div>
        <div class="w-8"><!-- Placeholder --></div>
    </header>

    <!-- Mobile Sidebar -->
    <div class="overlay" id="overlay"></div>
    <div class="mobile-sidebar" id="mobileSidebar">
        <div class="p-3 flex items-center justify-between border-b border-gray-700">
            <div class="flex items-center">
                <img src="https://cdn.jsdelivr.net/gh/vtzai2024/TinhMatDoXayDung@main/LOGO%20VUONG%20NEN%20TRONG%20SUOT%20-chu%20trang-small.png" alt="Logo VTZ Spaxe" class="h-8 w-8 mr-2">
                <div class="font-bold text-primary-light">VTZ Spaxe</div>
            </div>
            <button id="closeSidebar" class="p-2">
                <i class="fas fa-times text-xl text-gray-300"></i>
            </button>
        </div>
        <nav class="mt-2">
            <a href="#nhap-thong-tin" class="nav-item px-4 py-3 flex items-center active">
                <i class="fas fa-edit mr-3"></i>
                <span>Nhập thông tin</span>
            </a>
            <a href="#ket-qua" class="nav-item px-4 py-3 flex items-center">
                <i class="fas fa-calculator mr-3"></i>
                <span>Kết quả tính toán</span>
            </a>
            <a href="#khai-toan" class="nav-item px-4 py-3 flex items-center">
                <i class="fas fa-file-invoice-dollar mr-3"></i>
                <span>Khái toán chi phí</span>
            </a>
            <a href="#huong-dan" class="nav-item px-4 py-3 flex items-center">
                <i class="fas fa-book mr-3"></i>
                <span>Hướng dẫn sử dụng</span>
            </a>
            <a href="#lien-he" class="nav-item px-4 py-3 flex items-center">
                <i class="fas fa-envelope mr-3"></i>
                <span>Liên hệ tư vấn</span>
            </a>
            <a href="#gioi-thieu" class="nav-item px-4 py-3 flex items-center">
                <i class="fas fa-building mr-3"></i>
                <span>Về chúng tôi</span>
            </a>
        </nav>
        <div class="p-3 text-xs text-gray-400 border-t border-gray-700 mt-3">
            QĐ số 56/2021/QĐ-UBND
        </div>
    </div>

    <!-- Main content -->
    <div class="content p-3">
        <!-- Tabs for main sections -->
        <div class="tab-container" id="mainTabs">
            <button class="tab-button active" data-target="nhap-thong-tin">Nhập dữ liệu</button>
            <button class="tab-button" data-target="ket-qua">Kết quả</button>
            <button class="tab-button" data-target="khai-toan">Khái toán</button>
            <button class="tab-button" data-target="huong-dan">Hướng dẫn</button>
        </div>

        <!-- Tab content -->
        <div class="tab-content active" id="nhap-thong-tin">
            <!-- Thông tin lô đất -->
            <div class="collapsible-section">
                <div class="collapsible-header">
                    <div class="font-bold text-sm">
                        <i class="fas fa-info-circle mr-2"></i> Thông tin lô đất
                    </div>
                    <i class="fas fa-chevron-down text-xs"></i>
                </div>
                <div class="collapsible-content expanded">
                    <div class="mb-3">
                        <label for="dienTichDat" class="form-label text-sm">Diện tích lô đất (m²)</label>
                        <input type="number" id="dienTichDat" class="form-input" placeholder="Nhập diện tích" min="0" step="0.01" inputmode="decimal">
                        <div id="dienTichDat-error" class="error-message"></div>
                    </div>
                    <div class="mb-3">
                        <label for="chieuSauDat" class="form-label text-sm">Chiều sâu lô đất (m)</label>
                        <input type="number" id="chieuSauDat" class="form-input" placeholder="Nhập chiều sâu" min="0" step="0.01" inputmode="decimal">
                        <div id="chieuSauDat-error" class="error-message"></div>
                    </div>
                    <div class="mb-3">
                        <label for="chieuRongLoGioi" class="form-label text-sm">Chiều rộng lộ giới (m)</label>
                        <input type="number" id="chieuRongLoGioi" class="form-input" placeholder="Nhập lộ giới" min="0" step="0.01" inputmode="decimal">
                        <div id="chieuRongLoGioi-error" class="error-message"></div>
                    </div>
                    <div class="mb-3">
                        <label for="chieuRongMatTien" class="form-label text-sm">Chiều rộng mặt tiền (m)</label>
                        <input type="number" id="chieuRongMatTien" class="form-input" placeholder="Nhập mặt tiền" min="0" step="0.01" inputmode="decimal">
                        <div id="chieuRongMatTien-error" class="error-message"></div>
                    </div>
                    <div class="mt-3">
                        <p class="form-label text-sm mb-2">Điều kiện đặc biệt:</p>
                        <div class="checkbox-item mb-2">
                            <input type="checkbox" id="quanTrungTam" name="viTri" class="mr-2">
                            <label for="quanTrungTam" class="text-sm">Thuộc Quận trung tâm</label>
                        </div>
                        <div class="checkbox-item mb-2">
                            <input type="checkbox" id="trucDuongThuongMai" name="viTri" class="mr-2">
                            <label for="trucDuongThuongMai" class="text-sm">Trục đường thương mại</label>
                        </div>
                        <div class="checkbox-item">
                            <input type="checkbox" id="matTienTren8m" name="viTri" class="mr-2">
                            <label for="matTienTren8m" class="text-sm">Mặt tiền > 8,0m</label>
                        </div>
                    </div>
                    <!-- Điều kiện hợp khối (chỉ hiển thị khi diện tích từ 15m² đến dưới 36m²) -->
                    <div id="hopKhoiSection" class="mt-3 hidden">
                        <div class="checkbox-item">
                            <input type="checkbox" id="hopKhoi" name="hopKhoi" class="mr-2">
                            <label for="hopKhoi" class="text-sm">Có điều kiện hợp khối kiến trúc hoặc mở rộng phía sau</label>
                        </div>
                        <div class="text-xs text-gray-400 mt-1 ml-8">Có các cạnh vuông góc/hình thang/hình đa giác với diện tích trên 36m²</div>
                    </div>
                </div>
            </div>

            <!-- Đơn giá thi công -->
            <div class="collapsible-section">
                <div class="collapsible-header">
                    <div class="font-bold text-sm">
                        <i class="fas fa-dollar-sign mr-2"></i> Đơn giá thi công
                    </div>
                    <i class="fas fa-chevron-down text-xs"></i>
                </div>
                <div class="collapsible-content">
                    <div class="mb-3">
                        <label for="donGiaThietKe" class="form-label text-sm">Đơn giá thiết kế (VNĐ/m²)</label>
                        <input type="text" id="donGiaThietKe" class="form-input currency-input" value="250.000" placeholder="VNĐ/m²" inputmode="decimal">
                    </div>
                    <div class="mb-3">
                        <label for="donGiaPhanTho" class="form-label text-sm">Đơn giá phần thô (VNĐ/m²)</label>
                        <input type="text" id="donGiaPhanTho" class="form-input currency-input" value="4.000.000" placeholder="VNĐ/m²" inputmode="decimal">
                    </div>
                    <div class="mb-3">
                        <label for="donGiaHoanThien" class="form-label text-sm">Đơn giá hoàn thiện (VNĐ/m²)</label>
                        <input type="text" id="donGiaHoanThien" class="form-input currency-input" value="2.500.000" placeholder="VNĐ/m²" inputmode="decimal">
                    </div>
                    <div class="mb-3">
                        <label for="donGiaNoiThat" class="form-label text-sm">Đơn giá nội thất (VNĐ/m²)</label>
                        <input type="text" id="donGiaNoiThat" class="form-input currency-input" value="2.000.000" placeholder="VNĐ/m²" inputmode="decimal">
                    </div>
                    <div class="mt-3">
                        <p class="form-label text-sm mb-2">Tùy chọn bổ sung:</p>
                        <div class="checkbox-item mb-2">
                            <input type="checkbox" id="coTangLung" name="tangLung" class="mr-2" checked>
                            <label for="coTangLung" class="text-sm">Có tầng lửng</label>
                            <div id="tangLungInfo" class="text-xs text-gray-400 mt-1">Chỉ khi lộ giới ≥ 6m</div>
                        </div>
                        <div class="checkbox-item mb-2">
                            <input type="checkbox" id="coTangDinhMai" name="tangDinhMai" class="mr-2" checked disabled>
                            <label for="coTangDinhMai" class="text-sm">Có tầng đỉnh mái</label>
                            <span class="ml-1 px-1 py-0.5 info-badge text-xs rounded">BT</span>
                        </div>
                        <div class="checkbox-item mb-2">
                            <input type="checkbox" id="coSanThuong" name="sanThuong" class="mr-2" checked>
                            <label for="coSanThuong" class="text-sm">Có sân thượng</label>
                        </div>
                        <div class="checkbox-item">
                            <input type="checkbox" id="coMaiBTCT" name="maiBTCT" class="mr-2" checked>
                            <label for="coMaiBTCT" class="text-sm">Có mái BTCT</label>
                        </div>
                    </div>
                </div>
            </div>

            <!-- Diện tích xây dựng -->
            <div class="collapsible-section">
                <div class="collapsible-header">
                    <div class="font-bold text-sm">
                        <i class="fas fa-ruler-combined mr-2"></i> Diện tích xây dựng
                    </div>
                    <i class="fas fa-chevron-down text-xs"></i>
                </div>
                <div class="collapsible-content">
                    <!-- Tầng hầm -->
                    <div class="construction-area-section">
                        <h3 class="construction-area-title">
                            <i class="fas fa-arrow-down mr-1"></i> Tầng hầm
                        </h3>
                        <div class="radio-group mb-2">
                            <div class="radio-item mb-1">
                                <input type="radio" name="tangHam" id="khongTangHam" value="none" checked class="mr-2">
                                <label for="khongTangHam" class="text-sm">Không có tầng hầm</label>
                            </div>
                            <div class="radio-item">
                                <input type="radio" name="tangHam" id="coTangHam" value="ham" class="mr-2">
                                <label for="coTangHam" class="text-sm">Có tầng hầm</label>
                            </div>
                        </div>
                        <div id="tangHamOptions" class="pl-2 mt-2 hidden">
                            <div class="construction-area-grid">
                                <div class="construction-radio-item">
                                    <input type="radio" name="doSauHam" id="doSau1" value="1.5">
                                    <label for="doSau1" class="radio-label">
                                        <span>1.0m - 1.3m</span>
                                        <span class="radio-coefficient">150%</span>
                                    </label>
                                </div>
                                <div class="construction-radio-item">
                                    <input type="radio" name="doSauHam" id="doSau2" value="1.7">
                                    <label for="doSau2" class="radio-label">
                                        <span>1.3m - 1.7m</span>
                                        <span class="radio-coefficient">170%</span>
                                    </label>
                                </div>
                                <div class="construction-radio-item">
                                    <input type="radio" name="doSauHam" id="doSau3" value="2.0">
                                    <label for="doSau3" class="radio-label">
                                        <span>1.7m - 2.0m</span>
                                        <span class="radio-coefficient">200%</span>
                                    </label>
                                </div>
                                <div class="construction-radio-item">
                                    <input type="radio" name="doSauHam" id="doSau4" value="2.2">
                                    <label for="doSau4" class="radio-label">
                                        <span>Trên 2.0m</span>
                                        <span class="radio-coefficient">220%</span>
                                    </label>
                                </div>
                            </div>
                            <div class="checkbox-item mt-2">
                                <input type="checkbox" id="hamNho" class="mr-2">
                                <label for="hamNho" class="text-sm">Hầm < 70m²</label>
                                <span class="ml-1 px-1 py-0.5 info-badge text-xs rounded">+20%</span>
                            </div>
                        </div>
                    </div>
                    
                    <!-- Móng -->
                    <div class="construction-area-section">
                        <h3 class="construction-area-title">
                            <i class="fas fa-arrow-down mr-1"></i> Móng
                        </h3>
                        <div class="construction-area-grid">
                            <div class="construction-radio-item">
                                <input type="radio" name="loaiMong" id="mongDon" value="0.3" checked>
                                <label for="mongDon" class="radio-label">
                                    <span>Móng đơn</span>
                                    <span class="radio-coefficient">30%</span>
                                </label>
                            </div>
                            <div class="construction-radio-item">
                                <input type="radio" name="loaiMong" id="mongCoc" value="0.5">
                                <label for="mongCoc" class="radio-label">
                                    <span>Móng cọc</span>
                                    <span class="radio-coefficient">50%</span>
                                </label>
                            </div>
                            <div class="construction-radio-item">
                                <input type="radio" name="loaiMong" id="mongBang" value="0.5">
                                <label for="mongBang" class="radio-label">
                                    <span>Móng băng</span>
                                    <span class="radio-coefficient">50%</span>
                                </label>
                            </div>
                            <div class="construction-radio-item">
                                <input type="radio" name="loaiMong" id="mongBe" value="0.8">
                                <label for="mongBe" class="radio-label">
                                    <span>Móng bè</span>
                                    <span class="radio-coefficient">80%</span>
                                </label>
                            </div>
                        </div>
                    </div>
                    
                    <!-- Mái -->
                    <div class="construction-area-section">
                        <h3 class="construction-area-title">
                            <i class="fas fa-home mr-1"></i> Mái
                        </h3>
                        <div class="construction-area-grid">
                            <div class="construction-radio-item">
                                <input type="radio" name="loaiMai" id="maiBTCT" value="0.5" checked>
                                <label for="maiBTCT" class="radio-label">
                                    <span>Mái BTCT</span>
                                    <span class="radio-coefficient">50%</span>
                                </label>
                            </div>
                            <div class="construction-radio-item">
                                <input type="radio" name="loaiMai" id="maiTon" value="0.3">
                                <label for="maiTon" class="radio-label">
                                    <span>Mái tôn</span>
                                    <span class="radio-coefficient">30%</span>
                                </label>
                            </div>
                            <div class="construction-radio-item">
                                <input type="radio" name="loaiMai" id="maiNgoi" value="0.7">
                                <label for="maiNgoi" class="radio-label">
                                    <span>Mái ngói</span>
                                    <span class="radio-coefficient">70%</span>
                                </label>
                            </div>
                            <div class="construction-radio-item">
                                <input type="radio" name="loaiMai" id="maiXienBTCT" value="0.8">
                                <label for="maiXienBTCT" class="radio-label">
                                    <span>Mái xiên BTCT</span>
                                    <span class="radio-coefficient">80%</span>
                                </label>
                            </div>
                        </div>
                    </div>
                </div>
            </div>

            <!-- Cảnh báo diện tích < 36m² -->
            <div id="smallLotWarning" class="small-lot-warning hidden">
                <div class="flex">
                    <div class="flex-shrink-0">
                        <i class="fas fa-exclamation-triangle text-red-dark"></i>
                    </div>
                    <div class="ml-3">
                        <h3 class="text-xs font-medium text-red-dark">Lô đất dưới 36m²</h3>
                        <p class="mt-1 text-xs text-gray-300">Lô đất của bạn có diện tích nhỏ hơn 36m² và phải tuân theo quy định đặc biệt về chiều cao và số tầng.</p>
                        <div id="smallLotDetails" class="mt-1 text-xs text-gray-300"></div>
                    </div>
                </div>
            </div>
        </div>

        <!-- Kết quả tính toán -->
        <div class="tab-content" id="ket-qua">
            <div id="smallLotAlert" class="p-2 alert-red border-l-4 mb-3 text-xs rounded hidden">
                <div class="flex">
                    <div class="flex-shrink-0">
                        <i class="fas fa-exclamation-triangle text-red-dark"></i>
                    </div>
                    <div class="ml-3">
                        <h3 class="text-xs font-medium text-red-dark">Lô đất dưới 36m²</h3>
                        <p id="smallLotDetails2" class="mt-1 text-gray-300"></p>
                    </div>
                </div>
            </div>

            <div class="result-section">
                <div class="result-title">
                    <i class="fas fa-ruler-combined mr-1"></i> Diện tích và mật độ
                </div>
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
            <div class="result-section">
                <div class="result-title">
                    <i class="fas fa-arrows-alt-h mr-1"></i> Khoảng lùi
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
            <div class="result-section">
                <div class="result-title">
                    <i class="fas fa-building mr-1"></i> Chiều cao và số tầng
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
            <div class="result-section">
                <div class="result-title">
                    <i class="fas fa-home mr-1"></i> Ban công và ô văng
                </div>
                <div class="result-row">
                    <span class="result-label">Độ vươn ban công:</span>
                    <span class="result-value" id="doVuonBanCong">--</span>
                </div>
                <div class="result-row">
                    <span class="result-label">Diện tích ban công:</span>
                    <span class="result-value" id="dienTichBanCong">--</span>
                </div>
            </div>
            <div class="p-2 alert-yellow border-l-4 mt-3 text-xs rounded">
                <div class="flex">
                    <div class="flex-shrink-0">
                        <i class="fas fa-exclamation-triangle text-yellow-dark"></i>
                    </div>
                    <div class="ml-3">
                        <h3 class="text-xs font-medium text-yellow-dark">Lưu ý quan trọng:</h3>
                        <p class="mt-1 text-gray-300">Kết quả mang tính tham khảo. Vui lòng liên hệ cơ quan có thẩm quyền để được hướng dẫn cụ thể.</p>
                    </div>
                </div>
            </div>
        </div>

        <!-- Khái toán chi phí -->
        <div class="tab-content" id="khai-toan">
            <div class="overflow-x-auto">
                <table class="khai-toan-table" id="khaiToanTable">
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
                            <td colspan="6" class="text-center py-4 text-xs">
                                Nhập thông tin và nhấn "Tính toán" để xem kết quả
                            </td>
                        </tr>
                    </tbody>
                </table>
            </div>
            <div class="mt-3 p-3 bg-blue-900 bg-opacity-30 rounded-lg">
                <div class="flex justify-between items-center mb-2">
                    <span class="font-medium text-xs">Chi phí thiết kế:</span>
                    <span id="chiPhiThietKe" class="font-semibold text-primary-light text-xs">--</span>
                </div>
                <div class="flex justify-between items-center mb-2">
                    <span class="font-medium text-xs">Chi phí phần thô:</span>
                    <span id="chiPhiPhanTho" class="font-semibold text-primary-light text-xs">--</span>
                </div>
                <div class="flex justify-between items-center mb-2">
                    <span class="font-medium text-xs">Chi phí hoàn thiện:</span>
                    <span id="chiPhiHoanThien" class="font-semibold text-primary-light text-xs">--</span>
                </div>
                <div class="flex justify-between items-center">
                    <span class="font-medium text-xs">Chi phí nội thất:</span>
                    <span id="chiPhiNoiThat" class="font-semibold text-primary-light text-xs">--</span>
                </div>
            </div>
            <div class="flex justify-between items-center mt-3 p-3 bg-green-900 bg-opacity-60 rounded-lg text-white">
                <span class="font-bold text-sm">Tổng chi phí:</span>
                <span id="tongChiPhi" class="font-bold text-sm">--</span>
            </div>
        </div>

        <!-- Hướng dẫn sử dụng -->
        <div class="tab-content" id="huong-dan">
            <div class="collapsible-section">
                <div class="collapsible-header">
                    <div class="font-bold text-sm">
                        <i class="fas fa-table mr-2"></i> Mật độ xây dựng
                    </div>
                    <i class="fas fa-chevron-down text-xs"></i>
                </div>
                <div class="collapsible-content">
                    <table class="khai-toan-table text-xs mb-2">
                        <tr>
                            <th>Diện tích lô đất (m²)</th>
                            <th>Mật độ tối đa (%)</th>
                        </tr>
                        <tr><td>≤ 50</td><td>100</td></tr>
                        <tr><td>100</td><td>90</td></tr>
                        <tr><td>200</td><td>70</td></tr>
                        <tr><td>300</td><td>60</td></tr>
                        <tr><td>500</td><td>50</td></tr>
                    </table>
                </div>
            </div>
            
            <div class="collapsible-section">
                <div class="collapsible-header">
                    <div class="font-bold text-sm">
                        <i class="fas fa-arrows-alt-h mr-2"></i> Khoảng lùi phía sau
                    </div>
                    <i class="fas fa-chevron-down text-xs"></i>
                </div>
                <div class="collapsible-content">
                    <ul class="list-disc pl-4 space-y-1 text-xs">
                        <li>D ≥ 16m: Khoảng lùi tối thiểu 2m</li>
                        <li>9m ≤ D < 16m: Khoảng lùi tối thiểu 1m</li>
                        <li>D < 9m: Khuyến khích tạo khoảng trống phía sau</li>
                    </ul>
                </div>
            </div>
            
            <div class="collapsible-section">
                <div class="collapsible-header">
                    <div class="font-bold text-sm">
                        <i class="fas fa-building mr-2"></i> Số tầng cao độ
                    </div>
                    <i class="fas fa-chevron-down text-xs"></i>
                </div>
                <div class="collapsible-content">
                    <ul class="list-disc pl-4 space-y-1 text-xs">
                        <li>L ≥ 25m: 6 tầng</li>
                        <li>16m ≤ L < 25m: 5 tầng + tầng cộng thêm (nếu có điều kiện)</li>
                        <li>6m ≤ L < 16m: 4 tầng + tầng cộng thêm (nếu có điều kiện)</li>
                        <li>3.5m ≤ L < 6m: 3 tầng + tầng cộng thêm (nếu có điều kiện)</li>
                        <li>L < 3.5m: 3 tầng (không cộng thêm)</li>
                    </ul>
                </div>
            </div>
            
            <div class="collapsible-section">
                <div class="collapsible-header">
                    <div class="font-bold text-sm">
                        <i class="fas fa-home mr-2"></i> Ban công và ô văng
                    </div>
                    <i class="fas fa-chevron-down text-xs"></i>
                </div>
                <div class="collapsible-content">
                    <table class="khai-toan-table text-xs">
                        <tr>
                            <th>Chiều rộng lộ giới (m)</th>
                            <th>Độ vươn tối đa (m)</th>
                        </tr>
                        <tr><td>L < 7</td><td>0</td></tr>
                        <tr><td>7 ≤ L < 12</td><td>0,9</td></tr>
                        <tr><td>12 ≤ L < 20</td><td>1,2</td></tr>
                        <tr><td>L ≥ 20</td><td>1,4</td></tr>
                    </table>
                </div>
            </div>

            <div class="collapsible-section">
                <div class="collapsible-header">
                    <div class="font-bold text-sm">
                        <i class="fas fa-ruler-vertical mr-2"></i> Quy định lô đất nhỏ
                    </div>
                    <i class="fas fa-chevron-down text-xs"></i>
                </div>
                <div class="collapsible-content">
                    <ul class="list-disc pl-4 space-y-1 text-xs">
                        <li>Lô đất tối thiểu 36m², chiều rộng mặt tiền và chiều sâu không nhỏ hơn 3,0m.</li>
                        <li>Lô đất có chiều rộng mặt tiền hoặc chiều sâu < 3,0m: cao tối đa 7,0m tại CGXD và 9,0m tại đỉnh mái.</li>
                        <li>Lô đất < 15m², có chiều rộng và chiều sâu ≥ 3,0m: cao tối đa 7,0m tại đỉnh mái.</li>
                        <li>Lô đất 15-36m², có chiều rộng và chiều sâu ≥ 3,0m:
                            <ul class="list-disc pl-4 mt-1">
                                <li>Lộ giới ≥ 6m: cao tối đa 11,6m tại CGXD và 13,6m tại đỉnh mái</li>
                                <li>Lộ giới < 6m: cao tối đa 11,6m tại đỉnh mái</li>
                            </ul>
                        </li>
                    </ul>
                </div>
            </div>
            
            <!-- Liên hệ tư vấn -->
            <div class="collapsible-section mt-5" id="lien-he">
                <div class="collapsible-header">
                    <div class="font-bold text-sm">
                        <i class="fas fa-envelope mr-2"></i> Liên hệ tư vấn
                    </div>
                    <i class="fas fa-chevron-down text-xs"></i>
                </div>
                <div class="collapsible-content">
                    <form>
                        <div class="mb-3">
                            <label for="hoTen" class="form-label text-sm">Họ và tên</label>
                            <input type="text" id="hoTen" class="form-input" placeholder="Nhập họ tên">
                        </div>
                        <div class="mb-3">
                            <label for="soDienThoai" class="form-label text-sm">Số điện thoại</label>
                            <input type="tel" id="soDienThoai" class="form-input" placeholder="Nhập SĐT" inputmode="tel">
                        </div>
                        <div class="mb-3">
                            <label for="noiDung" class="form-label text-sm">Nội dung</label>
                            <textarea id="noiDung" class="form-input" rows="3" placeholder="Nhập nội dung cần tư vấn"></textarea>
                        </div>
                        <button type="button" class="btn-primary px-4 py-2 rounded-lg w-full">
                            <i class="fas fa-paper-plane mr-2"></i> Gửi thông tin
                        </button>
                    </form>
                </div>
            </div>
            
            <!-- Về chúng tôi -->
            <div class="collapsible-section" id="gioi-thieu">
                <div class="collapsible-header">
                    <div class="font-bold text-sm">
                        <i class="fas fa-building mr-2"></i> Về chúng tôi
                    </div>
                    <i class="fas fa-chevron-down text-xs"></i>
                </div>
                <div class="collapsible-content">
                    <div class="flex flex-col items-center mb-3">
                        <img src="https://cdn.jsdelivr.net/gh/vtzai2024/TinhMatDoXayDung@main/LOGO%20VUONG%20NEN%20TRONG%20SUOT%20-chu%20trang-small.png" alt="Logo VTZ Spaxe" class="h-16 w-16 mb-2">
                        <div class="text-center">
                            <div class="font-bold text-sm">Công ty TNHH Thiết kế và xây dựng VTZ Spaxe</div>
                            <p class="text-xs text-gray-400">TIÊN PHONG - TẬN TÂM - TRUNG THỰC - TRÍ TUỆ</p>
                        </div>
                    </div>
                    <p class="text-xs mb-2">VTZ Spaxe chuyên thiết kế, thi công xây dựng nhà phố, biệt thự, căn hộ với chất lượng cao và thiết kế hiện đại.</p>
                </div>
            </div>
        </div>
    </div>

    <!-- Bottom Navigation Bar -->
    <div class="bottom-nav">
        <a href="#nhap-thong-tin" class="bottom-nav-item active" data-target="nhap-thong-tin">
            <i class="fas fa-edit"></i>
            <span>Nhập liệu</span>
        </a>
        <a href="#ket-qua" class="bottom-nav-item" data-target="ket-qua">
            <i class="fas fa-calculator"></i>
            <span>Kết quả</span>
        </a>
        <a href="#khai-toan" class="bottom-nav-item" data-target="khai-toan">
            <i class="fas fa-file-invoice-dollar"></i>
            <span>Khái toán</span>
        </a>
        <a href="#huong-dan" class="bottom-nav-item" data-target="huong-dan">
            <i class="fas fa-book"></i>
            <span>Hướng dẫn</span>
        </a>
    </div>

    <!-- Floating Action Button -->
    <button id="tinhToanBtn" class="fab">
        <i class="fas fa-calculator"></i>
    </button>

    <!-- Back to top button -->
    <button id="backToTop" class="back-to-top">
        <i class="fas fa-arrow-up"></i>
    </button>

    <script>
        // Xử lý sidebar di động
        const menuToggle = document.getElementById('menuToggle');
        const closeSidebar = document.getElementById('closeSidebar');
        const mobileSidebar = document.getElementById('mobileSidebar');
        const overlay = document.getElementById('overlay');
        const navItems = document.querySelectorAll('.nav-item');
        
        // Mở sidebar
        menuToggle.addEventListener('click', function() {
            mobileSidebar.classList.add('open');
            overlay.classList.add('active');
            document.body.style.overflow = 'hidden';
        });
        
        // Đóng sidebar
        function closeMobileSidebar() {
            mobileSidebar.classList.remove('open');
            overlay.classList.remove('active');
            document.body.style.overflow = '';
        }
        
        closeSidebar.addEventListener('click', closeMobileSidebar);
        overlay.addEventListener('click', closeMobileSidebar);
        
        // Đóng sidebar khi click vào mục điều hướng
        navItems.forEach(item => {
            item.addEventListener('click', function() {
                navItems.forEach(navItem => {
                    navItem.classList.remove('active');
                });
                this.classList.add('active');
                closeMobileSidebar();
            });
        });

        // Xử lý tabs
        const tabButtons = document.querySelectorAll('.tab-button');
        const tabContents = document.querySelectorAll('.tab-content');
        const bottomNavItems = document.querySelectorAll('.bottom-nav-item');
        
        function changeTab(targetId) {
            // Ẩn tất cả tab content
            tabContents.forEach(content => {
                content.classList.remove('active');
            });
            
            // Hiển thị tab content được chọn
            const targetContent = document.getElementById(targetId);
            if (targetContent) {
                targetContent.classList.add('active');
            }
            
            // Cập nhật trạng thái active của tab buttons
            tabButtons.forEach(button => {
                if (button.dataset.target === targetId) {
                    button.classList.add('active');
                } else {
                    button.classList.remove('active');
                }
            });
            
            // Cập nhật trạng thái active của bottom nav items
            bottomNavItems.forEach(item => {
                if (item.dataset.target === targetId) {
                    item.classList.add('active');
                } else {
                    item.classList.remove('active');
                }
            });
        }
        
        // Event listener cho tab buttons
        tabButtons.forEach(button => {
            button.addEventListener('click', function() {
                const targetId = this.dataset.target;
                changeTab(targetId);
            });
        });
        
        // Event listener cho bottom nav items
        bottomNavItems.forEach(item => {
            item.addEventListener('click', function(e) {
                e.preventDefault();
                const targetId = this.dataset.target;
                changeTab(targetId);
            });
        });

        // Xử lý collapsible sections
        const collapsibleHeaders = document.querySelectorAll('.collapsible-header');
        
        collapsibleHeaders.forEach(header => {
            header.addEventListener('click', function() {
                const content = this.nextElementSibling;
                const isExpanded = content.classList.contains('expanded');
                const icon = this.querySelector('i.fa-chevron-down');
                
                if (isExpanded) {
                    content.classList.remove('expanded');
                    icon.style.transform = 'rotate(0deg)';
                } else {
                    content.classList.add('expanded');
                    icon.style.transform = 'rotate(180deg)';
                }
            });
        });

        // Nút back to top
        const backToTopButton = document.getElementById('backToTop');
        
        window.addEventListener('scroll', function() {
            if (window.pageYOffset > 300) {
                backToTopButton.classList.add('show');
            } else {
                backToTopButton.classList.remove('show');
            }
        });
        
        backToTopButton.addEventListener('click', function() {
            window.scrollTo({
                top: 0,
                behavior: 'smooth'
            });
        });

        // Kiểm tra điều kiện lô đất dưới 36m²
        document.getElementById('dienTichDat').addEventListener('input', function() {
            const dienTichDat = parseFloat(this.value) || 0;
            const smallLotWarning = document.getElementById('smallLotWarning');
            const hopKhoiSection = document.getElementById('hopKhoiSection');
            
            if (dienTichDat > 0 && dienTichDat < 36) {
                smallLotWarning.classList.remove('hidden');
                
                // Hiển thị section hợp khối nếu diện tích từ 15-36m²
                if (dienTichDat >= 15 && dienTichDat < 36) {
                    hopKhoiSection.classList.remove('hidden');
                } else {
                    hopKhoiSection.classList.add('hidden');
                    document.getElementById('hopKhoi').checked = false;
                }
                
                // Cập nhật thông tin chi tiết
                updateSmallLotDetails(dienTichDat);
            } else {
                smallLotWarning.classList.add('hidden');
                hopKhoiSection.classList.add('hidden');
                document.getElementById('hopKhoi').checked = false;
            }
        });

        // Cập nhật thông tin chi tiết cho lô đất nhỏ
        function updateSmallLotDetails(dienTichDat) {
            const smallLotDetails = document.getElementById('smallLotDetails');
            let detailsText = '';
            
            if (dienTichDat < 15) {
                detailsText = 'Với diện tích dưới 15m², chiều cao sẽ bị giới hạn theo quy định đặc biệt.';
            } else if (dienTichDat >= 15 && dienTichDat < 36) {
                detailsText = 'Với diện tích từ 15m² đến dưới 36m², chiều cao tối đa sẽ phụ thuộc vào chiều rộng lộ giới và điều kiện hợp khối.';
            }
            
            smallLotDetails.textContent = detailsText;
        }

        // Hàm định dạng số với dấu chấm phần nghìn
        function formatNumber(number) {
            return number.toString().replace(/\B(?=(\d{3})+(?!\d))/g, ".");
        }

        // Hàm định dạng tiền tệ với VNĐ
        function formatCurrency(number) {
            return formatNumber(Math.round(number)) + ' VNĐ';
        }

        // Chuyển đổi chuỗi có định dạng về số
        function parseFormattedNumber(formattedNumber) {
            if (typeof formattedNumber === 'string') {
                return parseInt(formattedNumber.replace(/\./g, ''));
            }
            return formattedNumber;
        }

        // Hiển thị thông báo lỗi
        function showError(fieldId, message) {
            const errorElement = document.getElementById(`${fieldId}-error`);
            if (errorElement) {
                errorElement.textContent = message;
                errorElement.style.display = 'block';
                document.getElementById(fieldId).classList.add('border-red-500');
            }
        }

        // Ẩn thông báo lỗi
        function hideError(fieldId) {
            const errorElement = document.getElementById(`${fieldId}-error`);
            if (errorElement) {
                errorElement.style.display = 'none';
                document.getElementById(fieldId).classList.remove('border-red-500');
            }
        }

        // Hiển thị thông báo
        function showNotification(message, type) {
            const notification = document.createElement('div');
            notification.className = `notification ${type}`;
            notification.innerHTML = `
                <div class="notification-icon">
                    ${type === 'success' ? '✓' : '✗'}
                </div>
                <div class="notification-message">${message}</div>
            `;
            document.body.appendChild(notification);
            setTimeout(() => {
                notification.classList.add('show');
            }, 10);
            setTimeout(() => {
                notification.classList.remove('show');
                setTimeout(() => {
                    document.body.removeChild(notification);
                }, 300);
            }, 3000);
        }

        // Kiểm tra và cập nhật trạng thái tầng lửng dựa trên chiều rộng lộ giới
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

        // Kiểm tra yêu cầu đặc biệt cho lô đất nhỏ
        function kiemTraDieuKienDatNho(dienTichDat, chieuRongMatTien, chieuSauDat, chieuRongLoGioi, hopKhoi) {
            // Khởi tạo kết quả
            let result = {
                isSmallLot: false,
                specialHeight: false,
                heightRestriction: null,
                soTangToiDa: null,
                message: ""
            };
            
            // Kiểm tra nếu diện tích < 36m²
            if (dienTichDat < 36) {
                result.isSmallLot = true;
                
                // Trường hợp 1: Chiều rộng mặt tiền hoặc chiều sâu < 3.0m
                if (chieuRongMatTien < 3.0 || chieuSauDat < 3.0) {
                    result.specialHeight = true;
                    result.heightRestriction = {
                        taiCGXD: "7,0m",
                        taiDinhMai: "9,0m"
                    };
                    result.soTangToiDa = 2;
                    result.message = "Lô đất có chiều rộng mặt tiền hoặc chiều sâu nhỏ hơn 3,0m: chỉ được cải tạo, sửa chữa theo quy mô hiện trạng hoặc xây dựng mới với chiều cao tối đa tại CGXD 7,0m và đỉnh mái 9,0m.";
                }
                // Trường hợp 2: Diện tích < 15m², chiều rộng và chiều sâu >= 3.0m
                else if (dienTichDat < 15) {
                    result.specialHeight = true;
                    result.heightRestriction = {
                        taiCGXD: null,
                        taiDinhMai: "7,0m"
                    };
                    result.soTangToiDa = 2;
                    result.message = "Lô đất diện tích nhỏ hơn 15m², có chiều rộng mặt tiền và chiều sâu từ 3,0m trở lên: chỉ được cải tạo, sửa chữa theo hiện trạng hoặc xây dựng mới với chiều cao tối đa tại đỉnh mái không quá 7,0m.";
                }
                // Trường hợp 3: Diện tích từ 15-36m², chiều rộng và chiều sâu >= 3.0m
                else if (dienTichDat >= 15 && dienTichDat < 36) {
                    result.specialHeight = true;
                    
                    // Trường hợp 3a: Lộ giới >= 6m
                    if (chieuRongLoGioi >= 6) {
                        // Kiểm tra điều kiện hợp khối
                        if (hopKhoi) {
                            result.heightRestriction = {
                                taiCGXD: "11,6m",
                                taiDinhMai: "13,6m"
                            };
                            result.soTangToiDa = 3;
                            result.message = "Lô đất từ 15m² đến dưới 36m², có điều kiện hợp khối: được xây dựng với chiều cao tối đa tại CGXD 11,6m và đỉnh mái 13,6m.";
                        } else {
                            result.heightRestriction = {
                                taiCGXD: "11,6m",
                                taiDinhMai: "13,6m"
                            };
                            result.soTangToiDa = 3;
                            result.message = "Lô đất từ 15m² đến dưới 36m², tiếp giáp đường có lộ giới từ 6m trở lên: được xây dựng với chiều cao tối đa tại CGXD 11,6m và đỉnh mái 13,6m.";
                        }
                    } 
                    // Trường hợp 3b: Lộ giới < 6m
                    else {
                        result.heightRestriction = {
                            taiCGXD: null,
                            taiDinhMai: "11,6m"
                        };
                        result.soTangToiDa = 3;
                        result.message = "Lô đất từ 15m² đến dưới 36m², tiếp giáp đường có lộ giới nhỏ hơn 6m: được xây dựng với chiều cao tối đa tại đỉnh mái không quá 11,6m.";
                    }
                }
            }
            
            return result;
        }

        // Tính số tầng tối đa
        function tinhSoTangToiDa(chieuRongLoGioi, quanTrungTam, trucDuongThuongMai, matTienTren8m, dienTichDat, chieuRongMatTien, chieuSauDat, hopKhoi) {
            // Kiểm tra điều kiện đặc biệt cho lô đất < 36m²
            const dieuKienDatNho = kiemTraDieuKienDatNho(dienTichDat, chieuRongMatTien, chieuSauDat, chieuRongLoGioi, hopKhoi);
            
            if (dieuKienDatNho.specialHeight && dieuKienDatNho.soTangToiDa !== null) {
                return dieuKienDatNho.soTangToiDa;
            }
            
            // Tính toán bình thường nếu không có điều kiện đặc biệt
            let soTangCoBan = 0;
            let soTangCongThem = 0;

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
        function tinhChieuCaoToiDa(chieuRongLoGioi, soTang, dienTichDat, chieuRongMatTien, chieuSauDat, hopKhoi) {
            // Kiểm tra điều kiện đặc biệt cho lô đất < 36m²
            const dieuKienDatNho = kiemTraDieuKienDatNho(dienTichDat, chieuRongMatTien, chieuSauDat, chieuRongLoGioi, hopKhoi);
            
            if (dieuKienDatNho.specialHeight && dieuKienDatNho.heightRestriction !== null) {
                return dieuKienDatNho.heightRestriction;
            }
            
            // Tính toán bình thường nếu không có điều kiện đặc biệt
            let chieuCaoTaiCGXD = ""; // Chiều cao tại chỉ giới xây dựng
            let chieuCaoTaiDinhMai = ""; // Chiều cao tại đỉnh mái

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
                if (chieuRongLoGioi >= 25) {
                    return "Cho phép, cao tối đa 7,0m";
                } else if (chieuRongLoGioi >= 16) {
                    return "Cho phép, cao tối đa 7,0m";
                } else {
                    return "Cho phép, cao tối đa 5,8m";
                }
            } else {
                return "Không được phép (lộ giới < 6m)";
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
        function tinhKhaiToanChiPhi(dienTichDat, soTang, matDo, chieuRongLoGioi, chieuRongMatTien, chieuSauDat) {
            // Lấy trạng thái checkbox từ giao diện
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
            const dienTichXDMax = dienTichDat * matDo / 100;
            
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
                stt: stt,
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
                const isTotalRow = item.hangMuc.includes('Tổng');
                
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
                    checkbox.classList.add('build-checkbox');
                    checkbox.addEventListener('change', updateCostBasedOnSelection);
                    
                    // Nếu là tầng đỉnh mái thì không cho bỏ chọn
                    if (item.hangMuc === 'Tầng đỉnh mái') {
                        checkbox.disabled = true;
                        checkbox.checked = true;
                        const label = document.createElement('span');
                        label.textContent = ' BT';
                        label.style.fontSize = '0.7em';
                        label.style.color = 'var(--primary-light)';
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
            document.getElementById('chiPhiThietKe').innerHTML = `${formatCurrency(chiPhiThietKe)} <span class="percent-badge">${percentThietKe}%</span>`;
            document.getElementById('chiPhiPhanTho').innerHTML = `${formatCurrency(chiPhiPhanTho)} <span class="percent-badge">${percentPhanTho}%</span>`;
            document.getElementById('chiPhiHoanThien').innerHTML = `${formatCurrency(chiPhiHoanThien)} <span class="percent-badge">${percentHoanThien}%</span>`;
            document.getElementById('chiPhiNoiThat').innerHTML = `${formatCurrency(chiPhiNoiThat)} <span class="percent-badge">${percentNoiThat}%</span>`;
            document.getElementById('tongChiPhi').textContent = formatCurrency(tongChiPhi);
        }

        // Kiểm tra và sử dụng giá trị mặc định nếu cần
        function getFormattedPrice(inputElement, defaultValue) {
            const rawValue = inputElement.value.replace(/\./g, '');
            if (!rawValue || isNaN(parseFloat(rawValue))) {
                inputElement.value = formatNumber(defaultValue);
                return defaultValue;
            }
            return parseFloat(rawValue);
        }

        // Khởi tạo giá trị mặc định cho các trường đơn giá
        function setDefaultPrices() {
            const donGiaThietKeEl = document.getElementById('donGiaThietKe');
            const donGiaPhanThoEl = document.getElementById('donGiaPhanTho');
            const donGiaHoanThienEl = document.getElementById('donGiaHoanThien');
            const donGiaNoiThatEl = document.getElementById('donGiaNoiThat');
            
            if (!donGiaThietKeEl.value) {
                donGiaThietKeEl.value = formatNumber(250000);
            }
            if (!donGiaPhanThoEl.value) {
                donGiaPhanThoEl.value = formatNumber(4000000);
            }
            if (!donGiaHoanThienEl.value) {
                donGiaHoanThienEl.value = formatNumber(2500000);
            }
            if (!donGiaNoiThatEl.value) {
                donGiaNoiThatEl.value = formatNumber(2000000);
            }
        }

        // Xử lý sự kiện khi trang được tải
        document.addEventListener('DOMContentLoaded', function() {
            // Cập nhật trạng thái tầng lửng khi trang được tải
            const chieuRongLoGioi = parseFloat(document.getElementById('chieuRongLoGioi').value) || 0;
            updateTangLungAvailability(chieuRongLoGioi);
            
            // Xử lý sự kiện khi thay đổi chiều rộng lộ giới
            document.getElementById('chieuRongLoGioi').addEventListener('input', function() {
                const chieuRongLoGioi = parseFloat(this.value) || 0;
                updateTangLungAvailability(chieuRongLoGioi);
            });
            
            // Xử lý sự kiện khi thay đổi chiều rộng mặt tiền
            document.getElementById('chieuRongMatTien').addEventListener('input', function() {
                const chieuRongMatTien = parseFloat(this.value) || 0;
                if (chieuRongMatTien > 8.0) {
                    document.getElementById('matTienTren8m').checked = true;
                } else {
                    document.getElementById('matTienTren8m').checked = false;
                }
            });
            
            // Xử lý sự kiện khi thay đổi option tầng hầm
            document.querySelectorAll('input[name="tangHam"]').forEach(radio => {
                radio.addEventListener('change', function() {
                    const tangHamOptions = document.getElementById('tangHamOptions');
                    if (this.value === 'ham') {
                        tangHamOptions.classList.remove('hidden');
                        // Đảm bảo rằng có một độ sâu hầm được chọn
                        if (!document.querySelector('input[name="doSauHam"]:checked')) {
                            document.getElementById('doSau1').checked = true;
                        }
                    } else {
                        tangHamOptions.classList.add('hidden');
                    }
                });
            });
            
            // Định dạng các trường đơn giá khi blur
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
            
            // Thiết lập giá trị mặc định cho các trường đơn giá
            setDefaultPrices();
            
            // Xử lý sự kiện khi nhấn nút Tính toán
            document.getElementById('tinhToanBtn').addEventListener('click', function() {
                // Kiểm tra dữ liệu đầu vào
                let isValid = true;
                const dienTichDat = parseFloat(document.getElementById('dienTichDat').value);
                const chieuSauDat = parseFloat(document.getElementById('chieuSauDat').value);
                const chieuRongLoGioi = parseFloat(document.getElementById('chieuRongLoGioi').value);
                const chieuRongMatTien = parseFloat(document.getElementById('chieuRongMatTien').value);
                const hopKhoi = document.getElementById('hopKhoi').checked;
                
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
                
                // Đảm bảo các đơn giá có giá trị mặc định
                setDefaultPrices();
                
                if (!isValid) {
                    showNotification('Vui lòng nhập đầy đủ thông tin lô đất', 'error');
                    return;
                }
                
                // Tính toán
                // Lấy giá trị từ các checkbox
                const quanTrungTam = document.getElementById('quanTrungTam').checked;
                const trucDuongThuongMai = document.getElementById('trucDuongThuongMai').checked;
                const matTienTren8m = document.getElementById('matTienTren8m').checked || chieuRongMatTien > 8.0;
                
                // Tính mật độ xây dựng
                const matDo = tinhMatDoXayDung(dienTichDat);
                
                // Tính diện tích được xây dựng
                const dienTichXD = (dienTichDat * matDo / 100).toFixed(2);
                
                // Tính khoảng lùi phía sau
                const khoangLuiSau = tinhKhoangLuiSau(chieuSauDat);
                const khoangLuiSauText = getKhoangLuiSauText(chieuSauDat);
                
                // Tính diện tích sân sau
                const dienTichSanSau = (khoangLuiSau * chieuRongMatTien).toFixed(2);
                
                // Kiểm tra điều kiện đặc biệt cho lô đất < 36m²
                const dieuKienDatNho = kiemTraDieuKienDatNho(dienTichDat, chieuRongMatTien, chieuSauDat, chieuRongLoGioi, hopKhoi);
                
                // Tính số tầng tối đa
                const soTang = tinhSoTangToiDa(chieuRongLoGioi, quanTrungTam, trucDuongThuongMai, matTienTren8m, dienTichDat, chieuRongMatTien, chieuSauDat, hopKhoi);
                
                // Tính chiều cao tối đa
                const chieuCao = tinhChieuCaoToiDa(chieuRongLoGioi, soTang, dienTichDat, chieuRongMatTien, chieuSauDat, hopKhoi);
                
                // Xác định thông tin về tầng lửng
                const thongTinTangLung = xacDinhTangLung(chieuRongLoGioi);
                
                // Tính độ vươn của ban công
                const doVuonBanCong = tinhDoVuonBanCong(chieuRongLoGioi);
                const doVuonBanCongText = getDoVuonBanCongText(chieuRongLoGioi);
                
                // Tính diện tích ban công
                const dienTichBanCong = tinhDienTichBanCong(chieuRongLoGioi, chieuRongMatTien, soTang);
                
                // Tính khái toán chi phí
                const khaiToan = tinhKhaiToanChiPhi(dienTichDat, soTang, matDo, chieuRongLoGioi, chieuRongMatTien, chieuSauDat);
                
                // Hiển thị kết quả
                document.getElementById('dienTichLoDat').textContent = dienTichDat + ' m²';
                document.getElementById('dienTichXayDung').textContent = dienTichXD + ' m²';
                document.getElementById('matDoXayDung').textContent = matDo + ' %';
                document.getElementById('khoangLuiSau').textContent = khoangLuiSauText;
                document.getElementById('dienTichSanSau').textContent = dienTichSanSau + ' m²';
                document.getElementById('soTangToiDa').textContent = soTang + ' tầng';
                document.getElementById('chieuCaoToiDaTaiCGXD').textContent = chieuCao.taiCGXD || "Không quy định";
                document.getElementById('chieuCaoToiDaTaiDinhMai').textContent = chieuCao.taiDinhMai;
                document.getElementById('thongTinTangLung').textContent = thongTinTangLung;
                document.getElementById('doVuonBanCong').textContent = doVuonBanCongText;
                document.getElementById('dienTichBanCong').textContent = dienTichBanCong.toFixed(2) + ' m²';
                
                // Hiển thị cảnh báo lô đất dưới 36m² nếu cần
                const smallLotAlert = document.getElementById('smallLotAlert');
                const smallLotDetails2 = document.getElementById('smallLotDetails2');
                
                if (dieuKienDatNho.isSmallLot) {
                    smallLotAlert.classList.remove('hidden');
                    smallLotDetails2.textContent = dieuKienDatNho.message;
                } else {
                    smallLotAlert.classList.add('hidden');
                }
                
                // Hiển thị bảng khái toán
                renderKhaiToanTable(khaiToan.khaiToanTable);
                
                // Tính và hiển thị chi phí
                const donGiaThietKe = getFormattedPrice(document.getElementById('donGiaThietKe'), 250000);
                const donGiaPhanTho = getFormattedPrice(document.getElementById('donGiaPhanTho'), 4000000);
                const donGiaHoanThien = getFormattedPrice(document.getElementById('donGiaHoanThien'), 2500000);
                const donGiaNoiThat = getFormattedPrice(document.getElementById('donGiaNoiThat'), 2000000);
                
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
                document.getElementById('chiPhiThietKe').innerHTML = `${formatCurrency(chiPhiThietKe)} <span class="percent-badge">${percentThietKe}%</span>`;
                document.getElementById('chiPhiPhanTho').innerHTML = `${formatCurrency(chiPhiPhanTho)} <span class="percent-badge">${percentPhanTho}%</span>`;
                document.getElementById('chiPhiHoanThien').innerHTML = `${formatCurrency(chiPhiHoanThien)} <span class="percent-badge">${percentHoanThien}%</span>`;
                document.getElementById('chiPhiNoiThat').innerHTML = `${formatCurrency(chiPhiNoiThat)} <span class="percent-badge">${percentNoiThat}%</span>`;
                document.getElementById('tongChiPhi').textContent = formatCurrency(tongChiPhi);
                
                // Hiển thị thông báo thành công
                showNotification('Đã tính toán thành công!', 'success');
                
                // Chuyển sang tab kết quả
                changeTab('ket-qua');
            });
        });
    </script>
</body>
</html>

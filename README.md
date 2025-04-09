<!DOCTYPE html>
<html lang="vi">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Máy tính Quy định xây dựng TP. HCM - VTZ Spaxe</title>
    <link href="https://cdn.jsdelivr.net/npm/tailwindcss@2.2.19/dist/tailwind.min.css" rel="stylesheet">
    <link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/@fortawesome/fontawesome-free@6.0.0/css/all.min.css">
    <style>
        :root {
            --primary: #3B82F6;
            --primary-dark: #2563EB;
            --green: #10B981;
            --green-dark: #059669;
            --background: #FFFFFF;
            --background-alt: #F9FAFB;
            --text-primary: #111827;
            --text-secondary: #6B7280;
            --border-color: #E5E7EB;
        }
        
        body {
            font-family: 'Segoe UI', Arial, sans-serif;
            background-color: var(--background);
            color: var(--text-primary);
        }
        
        .sidebar {
            background-color: var(--background-alt);
            border-right: 1px solid var(--border-color);
        }
        
        .nav-item {
            color: var(--text-secondary);
            border-left: 3px solid transparent;
            transition: all 0.2s ease;
        }
        
        .nav-item:hover {
            background-color: rgba(59, 130, 246, 0.1);
            color: var(--primary);
            border-left-color: var(--primary);
        }
        
        .nav-item.active {
            background-color: rgba(59, 130, 246, 0.1);
            color: var(--primary);
            border-left-color: var(--primary);
            font-weight: 500;
        }
        
        .card {
            background-color: var(--background);
            border: 1px solid var(--border-color);
            border-radius: 0.5rem;
            box-shadow: 0 1px 3px rgba(0, 0, 0, 0.05);
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
        
        .checkbox-item input[type="checkbox"] {
            accent-color: var(--primary);
        }
        
        .form-input {
            border: 1px solid var(--border-color);
            border-radius: 0.375rem;
            padding: 0.5rem 0.75rem;
            width: 100%;
            color: var(--text-primary);
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
            font-size: 0.875rem;
            margin-top: 0.25rem;
        }
        
        .tab-container {
            border-bottom: 1px solid var(--border-color);
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
        
        .result-section {
            margin-bottom: 1.5rem;
        }
        
        .result-title {
            color: var(--primary);
            font-weight: 600;
            border-bottom: 1px solid var(--border-color);
            padding-bottom: 0.5rem;
            margin-bottom: 1rem;
        }
        
        .result-row {
            display: flex;
            justify-content: space-between;
            margin-bottom: 0.5rem;
            padding-bottom: 0.5rem;
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
        
        .khai-toan-table {
            width: 100%;
            border-collapse: collapse;
        }
        
        .khai-toan-table th {
            background-color: var(--background-alt);
            color: var(--text-primary);
            font-weight: 600;
            text-align: left;
            padding: 0.75rem;
            border: 1px solid var(--border-color);
        }
        
        .khai-toan-table td {
            padding: 0.75rem;
            border: 1px solid var(--border-color);
            color: var(--text-primary);
        }
        
        .khai-toan-table tr:nth-child(even) {
            background-color: var(--background-alt);
        }
        
        .total-row {
            background-color: var(--primary) !important;
            color: white !important;
            font-weight: 600;
        }
        
        .total-row td {
            color: white !important;
        }
        
        .total-green-row {
            background-color: var(--green) !important;
            color: white !important;
            font-weight: 600;
        }
        
        .total-green-row td {
            color: white !important;
        }
        
        .notification {
            position: fixed;
            top: 20px;
            right: 20px;
            padding: 12px 20px;
            background-color: white;
            border-left: 4px solid var(--primary);
            box-shadow: 0 2px 8px rgba(0, 0, 0, 0.15);
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
        
        .notification-icon {
            margin-right: 12px;
            font-size: 18px;
            color: var(--primary);
        }
        
        .notification.error .notification-icon {
            color: #EF4444;
        }
        
        .notification.success .notification-icon {
            color: #10B981;
        }
        
        .error-message {
            color: #EF4444;
            font-size: 0.875rem;
            margin-top: 0.25rem;
            display: none;
        }
        
        .percent-badge {
            display: inline-block;
            background-color: #E5E7EB;
            color: #374151;
            padding: 0.15rem 0.4rem;
            border-radius: 0.375rem;
            font-size: 0.75rem;
            margin-left: 0.5rem;
            font-weight: 500;
        }
        
        /* Diện tích xây dựng styles */
        .construction-area-section {
            margin-bottom: 1.5rem;
            border-bottom: 1px solid var(--border-color);
            padding-bottom: 1rem;
        }
        
        .construction-area-title {
            font-weight: 600;
            color: var(--primary);
            margin-bottom: 0.75rem;
        }
        
        .construction-area-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(200px, 1fr));
            gap: 1rem;
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
        }
        
        .radio-coefficient {
            color: var(--primary);
            font-weight: 500;
            font-size: 0.875rem;
        }
        
        /* Responsive design */
        @media (max-width: 768px) {
            .sidebar {
                width: 100%;
                position: static;
                height: auto;
            }
            
            .content {
                margin-left: 0;
            }
            
            .hide-sm {
                display: none;
            }
        }
    </style>
</head>
<body class="min-h-screen flex">
    <!-- Sidebar -->
    <div class="sidebar fixed w-64 h-full overflow-y-auto">
        <div class="p-4 flex items-center border-b border-grey-200">
            <a href="https://vtzspaxe.com/" target="_blank" class="flex items-center">
                <img src="https://raw.githubusercontent.com/vtzai2024/TinhMatDoXayDung/refs/heads/main/LOGO%20VUONG%20NEN%20TRONG%20SUOT%20-chu%20trang-small.png" alt="Logo VTZ Spaxe" class="h-10 w-10 mr-2">
                <div>
                    <div class="font-bold text-lg text-primary">VTZ Spaxe</div>
                    <div class="text-xs text-gray-500">Thiết kế & Xây dựng</div>
                </div>
            </a>
        </div>
        <nav class="mt-4">
            <div class="px-4 mb-2 text-xs text-gray-500 uppercase">Thông tin chính</div>
            <a href="#thong-tin" class="nav-item px-4 py-3 flex items-center active">
                <i class="fas fa-info-circle mr-3"></i>
                <span>Thông tin lô đất</span>
            </a>
            <a href="#don-gia" class="nav-item px-4 py-3 flex items-center">
                <i class="fas fa-dollar-sign mr-3"></i>
                <span>Đơn giá thi công</span>
            </a>
            <a href="#dien-tich-xay-dung" class="nav-item px-4 py-3 flex items-center">
                <i class="fas fa-ruler-combined mr-3"></i>
                <span>Diện tích xây dựng</span>
            </a>
            <a href="#results" class="nav-item px-4 py-3 flex items-center">
                <i class="fas fa-calculator mr-3"></i>
                <span>Kết quả tính toán</span>
            </a>
            <a href="#khai-toan" class="nav-item px-4 py-3 flex items-center">
                <i class="fas fa-file-invoice-dollar mr-3"></i>
                <span>Khái toán chi phí</span>
            </a>
            <a href="#guide" class="nav-item px-4 py-3 flex items-center">
                <i class="fas fa-book mr-3"></i>
                <span>Hướng dẫn sử dụng</span>
            </a>
            <div class="px-4 mt-6 mb-2 text-xs text-gray-500 uppercase">Thông tin khác</div>
            <a href="#lien-he" class="nav-item px-4 py-3 flex items-center">
                <i class="fas fa-envelope mr-3"></i>
                <span>Liên hệ tư vấn</span>
            </a>
            <a href="#about" class="nav-item px-4 py-3 flex items-center">
                <i class="fas fa-building mr-3"></i>
                <span>Về chúng tôi</span>
            </a>
        </nav>
    </div>

    <!-- Main content -->
    <div class="content ml-64 flex-grow p-6">
        <header class="mb-6 flex justify-between items-center">
            <h1 class="text-2xl font-bold">
                Máy tính Quy định xây dựng TP. HCM
                <div class="text-sm font-normal text-gray-500">Theo Phụ lục 18 - Quyết định số 56/2021/QĐ-UBND</div>
            </h1>
            <button id="tinhToanBtn" class="btn-primary px-6 py-3 rounded-lg flex items-center">
                <i class="fas fa-calculator mr-2"></i>
                <span>Tính toán</span>
            </button>
        </header>

        <div class="grid grid-cols-1 lg:grid-cols-2 gap-6">
            <!-- Thông tin lô đất -->
            <section id="thong-tin" class="card p-6">
                <h2 class="text-xl font-bold mb-4 card-header pb-3">
                    <i class="fas fa-info-circle mr-2"></i> Thông tin lô đất
                </h2>
                <div class="mt-4">
                    <div class="mb-4">
                        <label for="dienTichDat" class="form-label">Diện tích lô đất (m²):</label>
                        <input type="number" id="dienTichDat" class="form-input" placeholder="Nhập diện tích lô đất" min="0" step="0.01">
                        <div class="input-hint">Diện tích lô đất ảnh hưởng đến mật độ xây dựng tối đa</div>
                        <div id="dienTichDat-error" class="error-message"></div>
                    </div>
                    <div class="mb-4">
                        <label for="chieuSauDat" class="form-label">Chiều sâu lô đất (m):</label>
                        <input type="number" id="chieuSauDat" class="form-input" placeholder="Nhập chiều sâu lô đất" min="0" step="0.01">
                        <div class="input-hint">Chiều sâu lô đất ảnh hưởng đến yêu cầu khoảng lùi</div>
                        <div id="chieuSauDat-error" class="error-message"></div>
                    </div>
                    <div class="mb-4">
                        <label for="chieuRongLoGioi" class="form-label">Chiều rộng lộ giới (m):</label>
                        <input type="number" id="chieuRongLoGioi" class="form-input" placeholder="Nhập chiều rộng lộ giới" min="0" step="0.01">
                        <div class="input-hint">Chiều rộng lộ giới ảnh hưởng đến số tầng, chiều cao và ban công</div>
                        <div id="chieuRongLoGioi-error" class="error-message"></div>
                    </div>
                    <div class="mb-4">
                        <label for="chieuRongMatTien" class="form-label">Chiều rộng mặt tiền (m):</label>
                        <input type="number" id="chieuRongMatTien" class="form-input" placeholder="Nhập chiều rộng mặt tiền" min="0" step="0.01">
                        <div id="chieuRongMatTien-error" class="error-message"></div>
                    </div>
                    <div class="mt-6">
                        <p class="font-medium mb-3">Điều kiện đặc biệt:</p>
                        <div class="checkbox-item mb-2">
                            <input type="checkbox" id="quanTrungTam" name="viTri" class="mr-2">
                            <label for="quanTrungTam">Thuộc Quận trung tâm hoặc Trung tâm cấp quận</label>
                        </div>
                        <div class="checkbox-item mb-2">
                            <input type="checkbox" id="trucDuongThuongMai" name="viTri" class="mr-2">
                            <label for="trucDuongThuongMai">Thuộc trục đường thương mại - dịch vụ</label>
                        </div>
                        <div class="checkbox-item">
                            <input type="checkbox" id="matTienTren8m" name="viTri" class="mr-2">
                            <label for="matTienTren8m">Có chiều rộng mặt tiền > 8,0m</label>
                        </div>
                    </div>
                </div>
            </section>

            <!-- Đơn giá thi công -->
            <section id="don-gia" class="card p-6">
                <h2 class="text-xl font-bold mb-4 card-header pb-3">
                    <i class="fas fa-dollar-sign mr-2"></i> Đơn giá thi công
                </h2>
                <div class="mt-4">
                    <div class="mb-4">
                        <label for="donGiaThietKe" class="form-label">Đơn giá thiết kế (VNĐ/m²):</label>
                        <input type="text" id="donGiaThietKe" class="form-input currency-input" value="250.000" placeholder="VNĐ/m²">
                    </div>
                    <div class="mb-4">
                        <label for="donGiaPhanTho" class="form-label">Đơn giá phần thô (VNĐ/m²):</label>
                        <input type="text" id="donGiaPhanTho" class="form-input currency-input" value="4.000.000" placeholder="VNĐ/m²">
                    </div>
                    <div class="mb-4">
                        <label for="donGiaHoanThien" class="form-label">Đơn giá hoàn thiện (VNĐ/m²):</label>
                        <input type="text" id="donGiaHoanThien" class="form-input currency-input" value="2.500.000" placeholder="VNĐ/m²">
                    </div>
                    <div class="mb-4">
                        <label for="donGiaNoiThat" class="form-label">Đơn giá hoàn thiện nội thất (VNĐ/m²):</label>
                        <input type="text" id="donGiaNoiThat" class="form-input currency-input" value="2.000.000" placeholder="VNĐ/m²">
                    </div>
                    <div class="mt-6">
                        <p class="font-medium mb-3">Tùy chọn bổ sung:</p>
                        <div class="checkbox-item mb-2">
                            <input type="checkbox" id="coTangLung" name="tangLung" class="mr-2" checked>
                            <label for="coTangLung">Có tầng lửng</label>
                            <span id="tangLungInfo" class="ml-2 text-sm text-gray-500">Chỉ được phép khi chiều rộng lộ giới ≥ 6m</span>
                        </div>
                        <div class="checkbox-item mb-2">
                            <input type="checkbox" id="coTangDinhMai" name="tangDinhMai" class="mr-2" checked disabled>
                            <label for="coTangDinhMai">Có tầng đỉnh mái</label>
                            <span class="ml-2 px-2 py-0.5 bg-blue-100 text-primary text-xs rounded">Bắt buộc</span>
                        </div>
                        <div class="checkbox-item mb-2">
                            <input type="checkbox" id="coSanThuong" name="sanThuong" class="mr-2" checked>
                            <label for="coSanThuong">Có sân thượng</label>
                        </div>
                        <div class="checkbox-item">
                            <input type="checkbox" id="coMaiBTCT" name="maiBTCT" class="mr-2" checked>
                            <label for="coMaiBTCT">Có mái BTCT</label>
                        </div>
                    </div>
                </div>
            </section>
        </div>

        <!-- Diện tích xây dựng -->
        <section id="dien-tich-xay-dung" class="card p-6 mt-6">
            <h2 class="text-xl font-bold mb-4 card-header pb-3">
                <i class="fas fa-ruler-combined mr-2"></i> Diện tích xây dựng
            </h2>
            <div class="mt-4">
                <!-- Tầng hầm -->
                <div class="construction-area-section">
                    <h3 class="construction-area-title">
                        <i class="fas fa-arrow-down mr-2"></i> Tầng hầm
                    </h3>
                    <div class="radio-group mb-2">
                        <label class="inline-flex items-center mr-4">
                            <input type="radio" name="tangHam" value="none" checked class="mr-2">
                            <span>Không có tầng hầm</span>
                        </label>
                        <label class="inline-flex items-center mr-4">
                            <input type="radio" name="tangHam" value="ham" class="mr-2">
                            <span>Có tầng hầm</span>
                        </label>
                    </div>
                    <div id="tangHamOptions" class="pl-4 mt-2 hidden">
                        <div class="construction-area-grid">
                            <div class="construction-radio-item">
                                <input type="radio" name="doSauHam" id="doSau1" value="1.5">
                                <label for="doSau1" class="radio-label">
                                    <span>Sâu 1.0m - 1.3m</span>
                                    <span class="radio-coefficient">150%</span>
                                </label>
                            </div>
                            <div class="construction-radio-item">
                                <input type="radio" name="doSauHam" id="doSau2" value="1.7">
                                <label for="doSau2" class="radio-label">
                                    <span>Sâu 1.3m - 1.7m</span>
                                    <span class="radio-coefficient">170%</span>
                                </label>
                            </div>
                            <div class="construction-radio-item">
                                <input type="radio" name="doSauHam" id="doSau3" value="2.0">
                                <label for="doSau3" class="radio-label">
                                    <span>Sâu 1.7m - 2.0m</span>
                                    <span class="radio-coefficient">200%</span>
                                </label>
                            </div>
                            <div class="construction-radio-item">
                                <input type="radio" name="doSauHam" id="doSau4" value="2.2">
                                <label for="doSau4" class="radio-label">
                                    <span>Sâu trên 2.0m</span>
                                    <span class="radio-coefficient">220%</span>
                                </label>
                            </div>
                        </div>
                        <div class="checkbox-item mt-2">
                            <input type="checkbox" id="hamNho" class="mr-2">
                            <label for="hamNho">Hầm có diện tích sử dụng < 70m²</label>
                            <span class="ml-2 px-2 py-0.5 bg-blue-100 text-primary text-xs rounded">+20%</span>
                        </div>
                    </div>
                </div>
                
                <!-- Móng -->
                <div class="construction-area-section">
                    <h3 class="construction-area-title">
                        <i class="fas fa-arrow-down mr-2"></i> Móng
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
                        <i class="fas fa-home mr-2"></i> Mái
                    </h3>
                    <div class="construction-area-grid">
                        <div class="construction-radio-item">
                            <input type="radio" name="loaiMai" id="maiBTCT" value="0.5" checked>
                            <label for="maiBTCT" class="radio-label">
                                <span>Mái bê tông cốt thép</span>
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
                                <span>Mái ngói kèo sắt</span>
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
        </section>

        <!-- Kết quả tính toán -->
        <section id="results" class="card p-6 mt-6">
            <h2 class="text-xl font-bold mb-4 card-header pb-3">
                <i class="fas fa-calculator mr-2"></i> Kết quả tính toán
            </h2>
            <div class="grid grid-cols-1 md:grid-cols-2 gap-6 mt-4">
                <div class="result-section">
                    <div class="result-title">
                        <i class="fas fa-ruler-combined mr-2"></i> Diện tích và mật độ xây dựng
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
                        <i class="fas fa-arrows-alt-h mr-2"></i> Khoảng lùi
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
                        <i class="fas fa-building mr-2"></i> Chiều cao và số tầng
                    </div>
                    <div class="result-row">
                        <span class="result-label">Số tầng tối đa:</span>
                        <span class="result-value" id="soTangToiDa">--</span>
                    </div>
                    <div class="result-row">
                        <span class="result-label">Chiều cao tối đa tại CGXD:</span>
                        <span class="result-value" id="chieuCaoToiDaTaiCGXD">--</span>
                    </div>
                    <div class="result-row">
                        <span class="result-label">Chiều cao tối đa tại đỉnh mái:</span>
                        <span class="result-value" id="chieuCaoToiDaTaiDinhMai">--</span>
                    </div>
                    <div class="result-row">
                        <span class="result-label">Tầng lửng:</span>
                        <span class="result-value" id="thongTinTangLung">--</span>
                    </div>
                </div>
                <div class="result-section">
                    <div class="result-title">
                        <i class="fas fa-home mr-2"></i> Ban công và ô văng
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
            <div class="p-4 bg-yellow-50 border-l-4 border-yellow-400 mt-6">
                <div class="flex">
                    <div class="flex-shrink-0">
                        <i class="fas fa-exclamation-triangle text-yellow-600"></i>
                    </div>
                    <div class="ml-3">
                        <h3 class="text-sm font-medium text-yellow-800">Lưu ý quan trọng:</h3>
                        <div class="mt-2 text-sm text-yellow-700">
                            <p>Kết quả tính toán chỉ mang tính tham khảo theo quy định tại Phụ lục 18 - Quyết định số 56/2021/QĐ-UBND.</p>
                            <p class="mt-1">Vui lòng liên hệ cơ quan có thẩm quyền để được hướng dẫn cụ thể khi thực hiện xây dựng.</p>
                        </div>
                    </div>
                </div>
            </div>
        </section>

        <!-- Khái toán chi phí -->
        <section id="khai-toan" class="card p-6 mt-6">
            <h2 class="text-xl font-bold mb-4 card-header pb-3">
                <i class="fas fa-file-invoice-dollar mr-2"></i> Khái toán chi phí xây dựng
            </h2>
            <div class="overflow-x-auto mt-4">
                <table class="khai-toan-table" id="khaiToanTable">
                    <thead>
                        <tr>
                            <th>STT</th>
                            <th>Hạng mục</th>
                            <th>Diện tích cơ sở (m²)</th>
                            <th>Hệ số</th>
                            <th>Diện tích XD (m²)</th>
                            <th>Xây dựng</th>
                        </tr>
                    </thead>
                    <tbody id="khaiToanBody">
                        <tr>
                            <td colspan="6" class="text-center py-4">
                                Nhập thông tin và nhấn nút "Tính toán" để xem kết quả
                            </td>
                        </tr>
                    </tbody>
                </table>
            </div>
            <div class="grid grid-cols-1 md:grid-cols-2 gap-6 mt-6 bg-blue-50 p-4 rounded-lg">
                <div>
                    <div class="flex justify-between items-center mb-3">
                        <span class="font-medium">Chi phí thiết kế:</span>
                        <span id="chiPhiThietKe" class="font-semibold text-primary">--</span>
                    </div>
                    <div class="flex justify-between items-center mb-3">
                        <span class="font-medium">Chi phí phần thô:</span>
                        <span id="chiPhiPhanTho" class="font-semibold text-primary">--</span>
                    </div>
                </div>
                <div>
                    <div class="flex justify-between items-center mb-3">
                        <span class="font-medium">Chi phí hoàn thiện:</span>
                        <span id="chiPhiHoanThien" class="font-semibold text-primary">--</span>
                    </div>
                    <div class="flex justify-between items-center mb-3">
                        <span class="font-medium">Chi phí hoàn thiện nội thất:</span>
                        <span id="chiPhiNoiThat" class="font-semibold text-primary">--</span>
                    </div>
                </div>
            </div>
            <div class="flex justify-between items-center mt-4 p-3 bg-green-500 rounded-lg text-white">
                <span class="font-bold text-lg">Tổng chi phí:</span>
                <span id="tongChiPhi" class="font-bold text-lg">--</span>
            </div>
            <div class="mt-4 text-sm text-gray-600">
                <h3 class="font-medium mb-2">Ghi chú:</h3>
                <ul class="list-disc pl-5 space-y-1">
                    <li>Chi phí thiết kế = Tổng diện tích thiết kế × Đơn giá thiết kế</li>
                    <li>Chi phí phần thô = Tổng diện tích xây dựng × Đơn giá phần thô</li>
                    <li>Chi phí hoàn thiện = Tổng diện tích xây dựng × Đơn giá hoàn thiện</li>
                    <li>Chi phí hoàn thiện nội thất = Tổng diện tích xây dựng × 0,85 × Đơn giá hoàn thiện nội thất</li>
                    <li>Chi phí trên chưa bao gồm thuế VAT và các chi phí phát sinh khác</li>
                    <li><span class="font-medium text-blue-600">Lưu ý:</span> Tổng diện tích thiết kế không bao gồm diện tích móng nhà</li>
                </ul>
            </div>
        </section>

        <!-- Hướng dẫn sử dụng -->
        <section id="guide" class="card p-6 mt-6">
            <h2 class="text-xl font-bold mb-4 card-header pb-3">
                <i class="fas fa-book mr-2"></i> Hướng dẫn sử dụng
            </h2>
            <div class="space-y-6 mt-4">
                <div>
                    <h3 class="font-bold text-lg mb-3">Mật độ xây dựng</h3>
                    <p class="mb-2">Được tính dựa trên diện tích lô đất theo Bảng 1 của Phụ lục 18:</p>
                    <div class="overflow-x-auto">
                        <table class="khai-toan-table">
                            <tr>
                                <th>Diện tích lô đất (m²)</th>
                                <th>Mật độ xây dựng tối đa (%)</th>
                            </tr>
                            <tr><td>≤ 50</td><td>100</td></tr>
                            <tr><td>100</td><td>90</td></tr>
                            <tr><td>200</td><td>70</td></tr>
                            <tr><td>300</td><td>60</td></tr>
                            <tr><td>500</td><td>50</td></tr>
                        </table>
                    </div>
                    <p class="mt-2 text-sm italic text-gray-600">Chú thích: Với diện tích đất nằm giữa các giá trị trong bảng, mật độ xây dựng được tính theo phương pháp nội suy.</p>
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
                    <p class="mb-2">Dựa trên chiều rộng lộ giới (L) và các điều kiện đặc biệt theo Bảng 2:</p>
                    <ul class="list-disc pl-5 space-y-1">
                        <li>L ≥ 25m: 6 tầng</li>
                        <li>16m ≤ L < 25m: 5 tầng + tầng cộng thêm (nếu có điều kiện)</li>
                        <li>6m ≤ L < 16m: 4 tầng + tầng cộng thêm (nếu có điều kiện)</li>
                        <li>3.5m ≤ L < 6m: 3 tầng + tầng cộng thêm (nếu có điều kiện)</li>
                        <li>L < 3.5m: 3 tầng (không cộng thêm)</li>
                    </ul>
                    <p class="mt-2 text-sm italic text-gray-600">Điều kiện cộng thêm tầng: Thuộc Quận trung tâm/Trung tâm cấp quận, thuộc trục đường thương mại - dịch vụ, hoặc có chiều rộng mặt tiền > 8.0m.</p>
                </div>
                <div>
                    <h3 class="font-bold text-lg mb-3">Chiều cao tại đỉnh mái</h3>
                    <p class="mb-2">Theo Bảng 3 của Phụ lục 18, chiều cao tối đa tại đỉnh mái phụ thuộc vào chiều rộng lộ giới và số tầng:</p>
                    <div class="overflow-x-auto">
                        <table class="khai-toan-table">
                            <tr>
                                <th>Chiều rộng lộ giới L (m)</th>
                                <th>Chiều cao tối đa tại đỉnh mái (m)</th>
                                <th>Chiều cao tối đa tại đỉnh mái (nếu có cộng tầng) (m)</th>
                            </tr>
                            <tr><td>L ≥ 25</td><td>25,0</td><td>27,0</td></tr>
                            <tr><td>16 ≤ L < 25</td><td>23,6</td><td>27,0</td></tr>
                            <tr><td>6 ≤ L < 16</td><td>19,0</td><td>22,4</td></tr>
                            <tr><td>3,5 ≤ L < 6</td><td>13,6</td><td>15,6</td></tr>
                            <tr><td>L < 3,5</td><td>11,6</td><td>-</td></tr>
                        </table>
                    </div>
                    <p class="mt-2 text-sm italic text-gray-600">Lưu ý quan trọng: Theo quy định, tầng đỉnh mái là bắt buộc và được tính vào chiều cao tối đa của công trình. Trong khái toán chi phí, tầng đỉnh mái luôn được tính với hệ số 0,35.</p>
                </div>
                <div>
                    <h3 class="font-bold text-lg mb-3">Ban công và ô văng</h3>
                    <p class="mb-2">Độ vươn của ban công, ô văng nhô ra trên không gian lộ giới phụ thuộc vào chiều rộng của lộ giới theo Bảng 4 mục 10:</p>
                    <div class="overflow-x-auto">
                        <table class="khai-toan-table">
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
                    <p class="mt-2 text-sm italic text-gray-600">Lưu ý: Độ vươn phải nhỏ hơn chiều rộng vỉa hè ít nhất 1,0m. Mặt dưới của ban công, ô văng phải cao hơn mặt vỉa hè hiện hữu ổn định tối thiểu 3,5m.</p>
                </div>
            </div>
        </section>

        <!-- Liên hệ tư vấn -->
        <section id="lien-he" class="card p-6 mt-6">
            <h2 class="text-xl font-bold mb-4 card-header pb-3">
                <i class="fas fa-envelope mr-2"></i> Liên hệ tư vấn
            </h2>
            <p class="mb-4">Vui lòng để lại thông tin liên hệ để được tư vấn miễn phí về dự án xây dựng của bạn.</p>
            <form>
                <div class="mb-4">
                    <label for="hoTen" class="form-label">Họ và tên:</label>
                    <input type="text" id="hoTen" class="form-input" placeholder="Nhập họ và tên">
                </div>
                <div class="mb-4">
                    <label for="soDienThoai" class="form-label">Số điện thoại:</label>
                    <input type="tel" id="soDienThoai" class="form-input" placeholder="Nhập số điện thoại">
                </div>
                <div class="mb-4">
                    <label for="email" class="form-label">Email:</label>
                    <input type="email" id="email" class="form-input" placeholder="Nhập địa chỉ email">
                </div>
                <div class="mb-4">
                    <label for="noiDung" class="form-label">Nội dung:</label>
                    <textarea id="noiDung" class="form-input" rows="4" placeholder="Nhập nội dung cần tư vấn"></textarea>
                </div>
                <button type="button" class="btn-primary px-6 py-2 rounded-lg">
                    <i class="fas fa-paper-plane mr-2"></i> Gửi thông tin
                </button>
            </form>
        </section>

        <!-- Về chúng tôi -->
        <section id="about" class="card p-6 mt-6">
            <h2 class="text-xl font-bold mb-4 card-header pb-3">
                <i class="fas fa-building mr-2"></i> Về chúng tôi
            </h2>
            <div class="flex flex-col md:flex-row items-center mb-6">
                <a href="https://vtzspaxe.com/" target="_blank" class="mb-4 md:mb-0 md:mr-6">
                    <img src="https://raw.githubusercontent.com/vtzai2024/TinhMatDoXayDung/refs/heads/main/LOGO%20VUONG%20NEN%20TRONG%20SUOT%20-chu%20trang-small.png" alt="VTZ Spaxe Logo" class="h-24 w-24">
                </a>
                <div>
                    <h3 class="text-lg font-bold">Công ty TNHH Thiết kế và xây dựng VTZ Spaxe</h3>
                    <p class="text-sm text-gray-600 mb-2">TIÊN PHONG - TẬN TÂM - TRÁCH NHIỆM - TRUNG THỰC - TRÍ TUỆ</p>
                    <p class="mb-2">VTZ Spaxe là đơn vị chuyên thiết kế, thi công xây dựng nhà phố, biệt thự, căn hộ với chất lượng cao và thiết kế hiện đại.</p>
                    <p>Với đội ngũ kiến trúc sư, kỹ sư giàu kinh nghiệm, chúng tôi cam kết mang đến những công trình đạt chất lượng và thẩm mỹ cao nhất, đúng tiến độ và chi phí hợp lý.</p>
                </div>
            </div>
            <div class="grid grid-cols-1 md:grid-cols-3 gap-6 mt-8">
                <div class="text-center">
                    <div class="h-12 w-12 bg-blue-100 text-primary rounded-full flex items-center justify-center mx-auto mb-4">
                        <i class="fas fa-drafting-compass text-xl"></i>
                    </div>
                    <h3 class="font-bold mb-2">Thiết kế kiến trúc</h3>
                    <p class="text-sm text-gray-600">Giải pháp thiết kế hiện đại, phù hợp công năng sử dụng</p>
                </div>
                <div class="text-center">
                    <div class="h-12 w-12 bg-blue-100 text-primary rounded-full flex items-center justify-center mx-auto mb-4">
                        <i class="fas fa-hard-hat text-xl"></i>
                    </div>
                    <h3 class="font-bold mb-2">Thi công xây dựng</h3>
                    <p class="text-sm text-gray-600">Đội ngũ kỹ sư giám sát chuyên nghiệp, thợ thi công lành nghề</p>
                </div>
                <div class="text-center">
                    <div class="h-12 w-12 bg-blue-100 text-primary rounded-full flex items-center justify-center mx-auto mb-4">
                        <i class="fas fa-couch text-xl"></i>
                    </div>
                    <h3 class="font-bold mb-2">Thiết kế nội thất</h3>
                    <p class="text-sm text-gray-600">Thiết kế và thi công nội thất theo phong cách riêng của bạn</p>
                </div>
            </div>
        </section>

        <footer class="mt-8 pt-6 border-t border-gray-200 text-center text-sm text-gray-600">
            <p>© 2025 - Công ty TNHH Thiết kế và xây dựng VTZ Spaxe. Đã đăng ký bản quyền.</p>
            <p class="mt-1">Ứng dụng tính toán thông số xây dựng theo QĐ-56-2021-UBND</p>
        </footer>
    </div>

    <script>
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
                tangLungInfo.classList.remove('text-gray-500');
            } else {
                // Nếu chiều rộng lộ giới ≥ 6m, được phép có tầng lửng
                tangLungCheckbox.disabled = false;
                tangLungInfo.classList.remove('text-red-500');
                tangLungInfo.classList.add('text-gray-500');
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

        // Tính số tầng tối đa
        function tinhSoTangToiDa(chieuRongLoGioi, quanTrungTam, trucDuongThuongMai, matTienTren8m) {
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
        function tinhChieuCaoToiDa(chieuRongLoGioi, soTang) {
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
                dienTichDatCell.textContent = item.dienTichDat ? item.dienTichDat.toFixed(2) : '';
                row.appendChild(dienTichDatCell);
                
                // Tạo cột Hệ số
                const heSoCell = document.createElement('td');
                heSoCell.textContent = item.heSo ? item.heSo : '';
                row.appendChild(heSoCell);
                
                // Tạo cột Diện tích XD
                const dienTichXDCell = document.createElement('td');
                dienTichXDCell.textContent = item.dienTichXD ? item.dienTichXD.toFixed(2) : '';
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
                        label.textContent = ' Bắt buộc';
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
            
            // Điều hướng đến các tab khi click vào nav-item
            document.querySelectorAll('.nav-item').forEach(item => {
                item.addEventListener('click', function(e) {
                    // Loại bỏ class active khỏi tất cả các nav-item
                    document.querySelectorAll('.nav-item').forEach(navItem => {
                        navItem.classList.remove('active');
                    });
                    
                    // Thêm class active cho nav-item được click
                    this.classList.add('active');
                });
            });
            
            // Xử lý sự kiện khi nhấn nút Tính toán
            document.getElementById('tinhToanBtn').addEventListener('click', function() {
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
                
                // Tính số tầng tối đa
                const soTang = tinhSoTangToiDa(chieuRongLoGioi, quanTrungTam, trucDuongThuongMai, matTienTren8m);
                
                // Tính chiều cao tối đa
                const chieuCao = tinhChieuCaoToiDa(chieuRongLoGioi, soTang);
                
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
                document.getElementById('chieuCaoToiDaTaiCGXD').textContent = chieuCao.taiCGXD;
                document.getElementById('chieuCaoToiDaTaiDinhMai').textContent = chieuCao.taiDinhMai;
                document.getElementById('thongTinTangLung').textContent = thongTinTangLung;
                document.getElementById('doVuonBanCong').textContent = doVuonBanCongText;
                document.getElementById('dienTichBanCong').textContent = dienTichBanCong.toFixed(2) + ' m²';
                
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
                
                // Cuộn trang đến mục kết quả
                document.getElementById('results').scrollIntoView({ behavior: 'smooth' });
            });
        });
    </script>
</body>
</html>

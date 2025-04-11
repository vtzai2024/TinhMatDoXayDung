<!DOCTYPE html>
<html lang="vi">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Dự Toán Xây Dựng - VTZ Spaxe</title>
    <link href="https://cdn.jsdelivr.net/npm/tailwindcss@2.2.19/dist/tailwind.min.css" rel="stylesheet">
    <link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/@fortawesome/fontawesome-free@6.0.0/css/all.min.css">
    <script src="https://cdn.jsdelivr.net/npm/chart.js@3.7.1/dist/chart.min.js"></script>
    <script src="https://cdn.jsdelivr.net/npm/xlsx@0.18.5/dist/xlsx.full.min.js"></script>
    <style>
        :root {
            --primary: #3b82f6;
            --primary-dark: #2563eb;
            --background: #f3f4f6;
            --card-bg: #ffffff;
            --header-bg: #1e40af;
            --text-primary: #1f2937;
            --text-secondary: #6b7280;
            --border-color: #e5e7eb;
        }
        
        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background-color: var(--background);
            color: var(--text-primary);
        }
        
        .app-header {
            background-color: var(--header-bg);
            color: white;
        }
        
        .card {
            background-color: var(--card-bg);
            border-radius: 0.5rem;
            box-shadow: 0 1px 3px rgba(0, 0, 0, 0.1);
        }
        
        .btn-primary {
            background-color: var(--primary);
            color: white;
            transition: all 0.2s;
        }
        
        .btn-primary:hover {
            background-color: var(--primary-dark);
        }
        
        .tab-active {
            border-bottom: 3px solid var(--primary);
            color: var(--primary);
            font-weight: 600;
        }
        
        table {
            width: 100%;
            border-collapse: collapse;
        }
        
        th {
            background-color: #f9fafb;
            text-align: left;
            padding: 0.75rem;
            font-weight: 600;
            border-bottom: 2px solid var(--border-color);
        }
        
        td {
            padding: 0.75rem;
            border-bottom: 1px solid var(--border-color);
        }
        
        .editable:hover {
            background-color: #f9fafb;
            cursor: pointer;
        }
        
        .notification {
            position: fixed;
            top: 1rem;
            right: 1rem;
            padding: 0.75rem 1rem;
            border-radius: 0.375rem;
            box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
            z-index: 50;
            transition: all 0.3s;
            transform: translateY(-100%);
            opacity: 0;
        }
        
        .notification.show {
            transform: translateY(0);
            opacity: 1;
        }
        
        .notification-success {
            background-color: #10b981;
            color: white;
        }
        
        .notification-error {
            background-color: #ef4444;
            color: white;
        }
        
        .search-results {
            position: absolute;
            background-color: white;
            border: 1px solid var(--border-color);
            border-radius: 0.375rem;
            box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
            max-height: 300px;
            overflow-y: auto;
            width: 100%;
            z-index: 10;
        }
        
        .search-result-item {
            padding: 0.75rem;
            border-bottom: 1px solid var(--border-color);
            cursor: pointer;
        }
        
        .search-result-item:hover {
            background-color: #f9fafb;
        }
        
        .material-badge {
            display: inline-block;
            padding: 0.25rem 0.5rem;
            font-size: 0.75rem;
            font-weight: 600;
            border-radius: 9999px;
            margin-right: 0.5rem;
        }
        
        .badge-ximang {
            background-color: #93c5fd;
            color: #1e40af;
        }
        
        .badge-cat {
            background-color: #fecaca;
            color: #b91c1c;
        }
        
        .badge-gach {
            background-color: #fde68a;
            color: #92400e;
        }
        
        .badge-khac {
            background-color: #d1d5db;
            color: #374151;
        }
        
        .chart-container {
            position: relative;
            height: 300px;
            margin-bottom: 2rem;
        }
        
        /* Modal styles */
        .modal {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background-color: rgba(0, 0, 0, 0.5);
            z-index: 100;
            align-items: center;
            justify-content: center;
        }
        
        .modal.active {
            display: flex;
        }
        
        .modal-content {
            background-color: white;
            border-radius: 0.5rem;
            max-width: 600px;
            width: 90%;
            max-height: 90vh;
            overflow-y: auto;
        }
        
        /* Print styles */
        @media print {
            body {
                background-color: white;
            }
            
            .no-print {
                display: none !important;
            }
            
            .print-break-inside-avoid {
                page-break-inside: avoid;
            }
            
            .card {
                box-shadow: none;
                border: 1px solid #ddd;
            }
        }
    </style>
</head>
<body class="pb-20">
    <!-- App Header -->
    <header class="app-header p-4 shadow-md">
        <div class="container mx-auto flex justify-between items-center">
            <div class="flex items-center">
                <div class="text-white font-bold text-xl">
                    <span>VTZ Spaxe</span>
                    <div class="text-sm font-normal opacity-80">Công ty TNHH Thiết kế và xây dựng</div>
                </div>
            </div>
            <div>
                <button id="exportExcelBtn" class="btn-primary px-4 py-2 rounded-lg text-sm flex items-center">
                    <i class="fas fa-file-excel mr-2"></i>Xuất Excel
                </button>
            </div>
        </div>
    </header>

    <!-- Main Content -->
    <main class="container mx-auto p-4">
        <!-- Project Info -->
        <div class="card p-4 mb-6">
            <h2 class="text-xl font-bold mb-4 pb-2 border-b border-gray-200">Thông tin dự án</h2>
            <div class="grid grid-cols-1 md:grid-cols-2 gap-4">
                <div>
                    <label class="block text-sm font-medium text-gray-700 mb-1">Tên dự án</label>
                    <input id="projectName" type="text" class="w-full p-2 border border-gray-300 rounded-md" value="Dự án mẫu" placeholder="Nhập tên dự án">
                </div>
                <div>
                    <label class="block text-sm font-medium text-gray-700 mb-1">Địa điểm</label>
                    <input id="projectLocation" type="text" class="w-full p-2 border border-gray-300 rounded-md" value="TP. Hồ Chí Minh" placeholder="Nhập địa điểm">
                </div>
            </div>
        </div>

        <!-- Tabs -->
        <div class="mb-6">
            <div class="border-b border-gray-200">
                <nav class="flex -mb-px">
                    <button class="tab-button tab-active px-4 py-2 text-sm font-medium" data-tab="dutoan">
                        <i class="fas fa-calculator mr-2"></i>Dự toán
                    </button>
                    <button class="tab-button px-4 py-2 text-sm font-medium text-gray-500" data-tab="vattu">
                        <i class="fas fa-boxes mr-2"></i>Vật tư tổng hợp
                    </button>
                    <button class="tab-button px-4 py-2 text-sm font-medium text-gray-500" data-tab="bieudo">
                        <i class="fas fa-chart-pie mr-2"></i>Biểu đồ phân tích
                    </button>
                </nav>
            </div>
        </div>

        <!-- Tab Contents -->
        <div class="tab-contents">
            <!-- Dự toán Tab -->
            <div id="dutoan-tab" class="tab-content active">
                <div class="card p-4 mb-6">
                    <div class="flex justify-between items-center mb-4">
                        <h2 class="text-xl font-bold">Bảng dự toán chi tiết</h2>
                        <button id="addWorkBtn" class="btn-primary px-3 py-2 rounded-md text-sm">
                            <i class="fas fa-plus mr-2"></i>Thêm công việc
                        </button>
                    </div>
                    
                    <div class="overflow-x-auto">
                        <table class="min-w-full">
                            <thead>
                                <tr>
                                    <th class="w-12">STT</th>
                                    <th class="w-32">Mã hiệu</th>
                                    <th>Tên công việc</th>
                                    <th class="w-24">Đơn vị</th>
                                    <th class="w-32">Khối lượng</th>
                                    <th class="w-40">Đơn giá (VNĐ)</th>
                                    <th class="w-48">Thành tiền (VNĐ)</th>
                                    <th class="w-20">Thao tác</th>
                                </tr>
                            </thead>
                            <tbody id="estimateTableBody">
                                <!-- Table content will be filled by JavaScript -->
                            </tbody>
                            <tfoot>
                                <tr class="bg-blue-50">
                                    <td colspan="6" class="text-right font-bold">Tổng cộng:</td>
                                    <td id="totalAmount" class="font-bold text-blue-600">0</td>
                                    <td></td>
                                </tr>
                            </tfoot>
                        </table>
                    </div>
                </div>
            </div>

            <!-- Vật tư Tab -->
            <div id="vattu-tab" class="tab-content hidden">
                <div class="card p-4 mb-6">
                    <div class="flex justify-between items-center mb-4">
                        <h2 class="text-xl font-bold">Bảng vật tư tổng hợp</h2>
                        <div class="flex">
                            <select id="materialFilter" class="mr-2 p-2 border border-gray-300 rounded-md text-sm">
                                <option value="all">Tất cả vật tư</option>
                                <option value="ximang">Xi măng</option>
                                <option value="cat">Cát</option>
                                <option value="gach">Gạch</option>
                                <option value="khac">Khác</option>
                            </select>
                            <button id="exportMaterialsBtn" class="btn-primary px-3 py-2 rounded-md text-sm">
                                <i class="fas fa-file-excel mr-2"></i>Xuất Excel
                            </button>
                        </div>
                    </div>
                    
                    <div class="overflow-x-auto">
                        <table class="min-w-full">
                            <thead>
                                <tr>
                                    <th class="w-12">STT</th>
                                    <th class="w-32">Nhóm</th>
                                    <th>Tên vật tư</th>
                                    <th class="w-24">Đơn vị</th>
                                    <th class="w-32">Khối lượng</th>
                                    <th class="w-40">Đơn giá (VNĐ)</th>
                                    <th class="w-48">Thành tiền (VNĐ)</th>
                                </tr>
                            </thead>
                            <tbody id="materialsTableBody">
                                <!-- Table content will be filled by JavaScript -->
                            </tbody>
                            <tfoot>
                                <tr class="bg-blue-50">
                                    <td colspan="6" class="text-right font-bold">Tổng cộng:</td>
                                    <td id="totalMaterialAmount" class="font-bold text-blue-600">0</td>
                                </tr>
                            </tfoot>
                        </table>
                    </div>
                </div>
            </div>

            <!-- Biểu đồ phân tích Tab -->
            <div id="bieudo-tab" class="tab-content hidden">
                <div class="grid grid-cols-1 lg:grid-cols-2 gap-6">
                    <div class="card p-4">
                        <h2 class="text-xl font-bold mb-4">Phân bổ chi phí theo nhóm vật tư</h2>
                        <div class="chart-container">
                            <canvas id="costDistributionChart"></canvas>
                        </div>
                    </div>
                    
                    <div class="card p-4">
                        <h2 class="text-xl font-bold mb-4">Top 10 vật tư chi phí cao nhất</h2>
                        <div class="chart-container">
                            <canvas id="top10MaterialsChart"></canvas>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </main>

    <!-- Add Work Modal -->
    <div id="addWorkModal" class="modal">
        <div class="modal-content p-6">
            <div class="flex justify-between items-center mb-4">
                <h3 class="text-lg font-bold">Thêm công việc</h3>
                <button class="close-modal text-gray-500 hover:text-gray-700">
                    <i class="fas fa-times"></i>
                </button>
            </div>
            
            <div class="mb-4">
                <label class="block text-sm font-medium text-gray-700 mb-1">Danh mục công việc</label>
                <select id="workCategory" class="w-full p-2 border border-gray-300 rounded-md">
                    <option value="all">Tất cả danh mục</option>
                    <option value="dat">Công tác đất</option>
                    <option value="mong">Công tác móng</option>
                    <option value="betong">Công tác bê tông</option>
                    <option value="xay">Công tác xây</option>
                    <option value="trat">Công tác trát</option>
                    <option value="latgach">Công tác lát gạch</option>
                    <option value="son">Công tác sơn</option>
                    <option value="mai">Công tác mái</option>
                    <option value="dien">Hệ thống điện</option>
                    <option value="nuoc">Hệ thống nước</option>
                    <option value="thietbivesinh">Thiết bị vệ sinh</option>
                    <option value="thachcao">Công tác thạch cao</option>
                    <option value="do">Đồ gỗ nội thất</option>
                    <option value="cua">Cửa các loại</option>
                    <option value="bep">Thiết bị bếp</option>
                </select>
            </div>
            
            <div class="mb-4">
                <label class="block text-sm font-medium text-gray-700 mb-1">Tìm kiếm công việc</label>
                <div class="relative">
                    <input id="workSearch" type="text" class="w-full p-2 border border-gray-300 rounded-md" placeholder="Nhập mã hiệu hoặc tên công việc">
                    <div id="searchResults" class="search-results hidden"></div>
                </div>
            </div>
            
            <div id="selectedWorkInfo" class="mb-4 p-3 bg-gray-50 rounded-md hidden">
                <div class="font-medium" id="selectedWorkName">Tên công việc</div>
                <div class="text-sm text-gray-600">
                    <span id="selectedWorkCode">Mã hiệu: </span>
                    <span class="mx-2">|</span>
                    <span id="selectedWorkUnit">Đơn vị: </span>
                </div>
                <div class="text-sm text-gray-600" id="selectedWorkPrice">Đơn giá: </div>
            </div>
            
            <div class="mb-4">
                <label class="block text-sm font-medium text-gray-700 mb-1">Khối lượng</label>
                <input id="workQuantity" type="number" step="0.01" min="0" class="w-full p-2 border border-gray-300 rounded-md" placeholder="Nhập khối lượng">
            </div>
            
            <div class="flex justify-end">
                <button class="close-modal px-4 py-2 border border-gray-300 rounded-md mr-2">Hủy</button>
                <button id="addWorkToEstimateBtn" class="btn-primary px-4 py-2 rounded-md">Thêm vào dự toán</button>
            </div>
        </div>
    </div>

    <!-- Notification -->
    <div id="notification" class="notification notification-success">
        <span id="notificationMessage">Thông báo</span>
    </div>

    <!-- Footer -->
    <footer class="bg-gray-800 text-white p-4 mt-8">
        <div class="container mx-auto">
            <div class="grid grid-cols-1 md:grid-cols-2 gap-4">
                <div>
                    <h3 class="text-lg font-bold mb-2">Công ty TNHH Thiết kế và xây dựng VTZ Spaxe</h3>
                    <p class="text-sm">TIÊN PHONG - TẬN TÂM - TRÁCH NHIỆM - TRUNG THỰC - TRÍ TUỆ</p>
                </div>
                <div class="text-sm text-right">
                    <p>Website: <a href="https://vtzspaxe.com" class="text-blue-300">vtzspaxe.com</a></p>
                    <p>Email: <a href="mailto:info@vtzspaxe.com" class="text-blue-300">info@vtzspaxe.com</a></p>
                    <p>Hotline: <a href="tel:0909123456" class="text-blue-300">0909 123 456</a></p>
                </div>
            </div>
        </div>
    </footer>

    <script>
        // Data
        const workItems = [
            // Công tác đất
            { code: "AB.11111", name: "Đào đất hố móng công trình", unit: "m³", price: 150000, category: "dat" },
            { code: "AB.11112", name: "Đào đất hố móng bằng máy đào", unit: "m³", price: 70000, category: "dat" },
            { code: "AB.11113", name: "Đắp đất nền công trình", unit: "m³", price: 180000, category: "dat" },
            { code: "AB.11114", name: "Vận chuyển đất đi đổ", unit: "m³", price: 120000, category: "dat" },
            { code: "AB.11115", name: "San nền bằng thủ công", unit: "m²", price: 35000, category: "dat" },
            
            // Công tác móng
            { code: "AB.21111", name: "Làm móng đơn BTCT", unit: "m³", price: 2800000, category: "mong" },
            { code: "AB.21112", name: "Làm móng băng BTCT", unit: "m³", price: 2600000, category: "mong" },
            { code: "AB.21113", name: "Làm móng bè BTCT", unit: "m³", price: 2750000, category: "mong" },
            { code: "AB.21114", name: "Đóng cọc bê tông", unit: "m", price: 450000, category: "mong" },
            { code: "AB.21115", name: "Đổ bê tông lót móng M100", unit: "m³", price: 1200000, category: "mong" },
            
            // Công tác bê tông
            { code: "AB.31111", name: "Đổ bê tông cột M250", unit: "m³", price: 2950000, category: "betong" },
            { code: "AB.31112", name: "Đổ bê tông dầm M250", unit: "m³", price: 2850000, category: "betong" },
            { code: "AB.31113", name: "Đổ bê tông sàn M250", unit: "m³", price: 2800000, category: "betong" },
            { code: "AB.31114", name: "Đổ bê tông móng M250", unit: "m³", price: 2750000, category: "betong" },
            { code: "AB.31115", name: "Làm coffa cột", unit: "m²", price: 220000, category: "betong" },
            { code: "AB.31116", name: "Làm coffa dầm", unit: "m²", price: 230000, category: "betong" },
            { code: "AB.31117", name: "Làm coffa sàn", unit: "m²", price: 200000, category: "betong" },
            { code: "AB.31118", name: "Gia công lắp đặt thép", unit: "kg", price: 25000, category: "betong" },
            
            // Công tác xây
            { code: "AB.41111", name: "Xây tường gạch đặc 100mm", unit: "m²", price: 320000, category: "xay" },
            { code: "AB.41112", name: "Xây tường gạch đặc 200mm", unit: "m²", price: 480000, category: "xay" },
            { code: "AB.41113", name: "Xây tường gạch hai lỗ 100mm", unit: "m²", price: 290000, category: "xay" },
            { code: "AB.41114", name: "Xây tường gạch hai lỗ 200mm", unit: "m²", price: 420000, category: "xay" },
            { code: "AB.41115", name: "Xây tường gạch block", unit: "m²", price: 350000, category: "xay" },
            
            // Công tác trát
            { code: "AB.51111", name: "Trát tường trong nhà dày 15mm", unit: "m²", price: 120000, category: "trat" },
            { code: "AB.51112", name: "Trát tường ngoài nhà dày 20mm", unit: "m²", price: 140000, category: "trat" },
            { code: "AB.51113", name: "Trát trần dày 15mm", unit: "m²", price: 130000, category: "trat" },
            { code: "AB.51114", name: "Trát cột dày 15mm", unit: "m²", price: 135000, category: "trat" },
            
            // Công tác lát gạch
            { code: "AB.61111", name: "Lát gạch ceramic 30x30cm nền", unit: "m²", price: 280000, category: "latgach" },
            { code: "AB.61112", name: "Lát gạch ceramic 40x40cm nền", unit: "m²", price: 300000, category: "latgach" },
            { code: "AB.61113", name: "Lát gạch granite 60x60cm nền", unit: "m²", price: 380000, category: "latgach" },
            { code: "AB.61114", name: "Ốp gạch ceramic 30x60cm tường", unit: "m²", price: 320000, category: "latgach" },
            { code: "AB.61115", name: "Ốp gạch ceramic 25x40cm tường", unit: "m²", price: 290000, category: "latgach" },
            
            // Công tác sơn
            { code: "AB.71111", name: "Sơn nước trong nhà 3 nước", unit: "m²", price: 75000, category: "son" },
            { code: "AB.71112", name: "Sơn nước ngoài nhà 3 nước", unit: "m²", price: 85000, category: "son" },
            { code: "AB.71113", name: "Bả matit tường trong nhà", unit: "m²", price: 45000, category: "son" },
            { code: "AB.71114", name: "Bả matit tường ngoài nhà", unit: "m²", price: 55000, category: "son" },
            { code: "AB.71115", name: "Sơn dầu cửa gỗ", unit: "m²", price: 120000, category: "son" },
            
            // Công tác mái
            { code: "AB.81111", name: "Lợp mái ngói đất nung", unit: "m²", price: 290000, category: "mai" },
            { code: "AB.81112", name: "Lợp mái tôn lạnh mạ kẽm", unit: "m²", price: 220000, category: "mai" },
            { code: "AB.81113", name: "Lợp mái tôn mạ màu", unit: "m²", price: 250000, category: "mai" },
            { code: "AB.81114", name: "Đổ mái BTCT dày 10cm", unit: "m³", price: 2800000, category: "mai" },
            { code: "AB.81115", name: "Chống thấm mái", unit: "m²", price: 180000, category: "mai" },
            
            // Hệ thống điện
            { code: "AC.11111", name: "Đi dây điện trong tường", unit: "m", price: 35000, category: "dien" },
            { code: "AC.11112", name: "Đi dây điện trong ống ruột gà", unit: "m", price: 45000, category: "dien" },
            { code: "AC.11113", name: "Lắp đặt ổ cắm đơn", unit: "cái", price: 120000, category: "dien" },
            { code: "AC.11114", name: "Lắp đặt ổ cắm đôi", unit: "cái", price: 150000, category: "dien" },
            { code: "AC.11115", name: "Lắp đặt công tắc đơn", unit: "cái", price: 110000, category: "dien" },
            { code: "AC.11116", name: "Lắp đặt công tắc đôi", unit: "cái", price: 140000, category: "dien" },
            { code: "AC.11117", name: "Lắp đặt đèn downlight", unit: "cái", price: 180000, category: "dien" },
            { code: "AC.11118", name: "Lắp đặt đèn led âm trần", unit: "cái", price: 210000, category: "dien" },
            { code: "AC.11119", name: "Lắp đặt đèn ốp trần", unit: "cái", price: 190000, category: "dien" },
            { code: "AC.11120", name: "Lắp đặt tủ điện", unit: "cái", price: 1500000, category: "dien" },
            
            // Hệ thống nước
            { code: "AC.21111", name: "Đi ống nước PPR 21mm", unit: "m", price: 75000, category: "nuoc" },
            { code: "AC.21112", name: "Đi ống nước PPR 27mm", unit: "m", price: 90000, category: "nuoc" },
            { code: "AC.21113", name: "Đi ống thoát nước PVC 60mm", unit: "m", price: 85000, category: "nuoc" },
            { code: "AC.21114", name: "Đi ống thoát nước PVC 90mm", unit: "m", price: 110000, category: "nuoc" },
            { code: "AC.21115", name: "Đi ống thoát nước PVC 114mm", unit: "m", price: 140000, category: "nuoc" },
            { code: "AC.21116", name: "Lắp đặt van khóa nước", unit: "cái", price: 120000, category: "nuoc" },
            
            // Thiết bị vệ sinh
            { code: "AC.31111", name: "Lắp đặt bồn cầu", unit: "bộ", price: 850000, category: "thietbivesinh" },
            { code: "AC.31112", name: "Lắp đặt lavabo", unit: "bộ", price: 650000, category: "thietbivesinh" },
            { code: "AC.31113", name: "Lắp đặt vòi sen", unit: "bộ", price: 450000, category: "thietbivesinh" },
            { code: "AC.31114", name: "Lắp đặt vòi rửa", unit: "cái", price: 350000, category: "thietbivesinh" },
            { code: "AC.31115", name: "Lắp đặt gương phòng tắm", unit: "cái", price: 380000, category: "thietbivesinh" },
            { code: "AC.31116", name: "Lắp đặt phụ kiện phòng tắm", unit: "bộ", price: 420000, category: "thietbivesinh" },
            
            // Công tác thạch cao
            { code: "AD.11111", name: "Làm trần thạch cao phẳng", unit: "m²", price: 220000, category: "thachcao" },
            { code: "AD.11112", name: "Làm trần thạch cao giật cấp", unit: "m²", price: 280000, category: "thachcao" },
            { code: "AD.11113", name: "Làm vách ngăn thạch cao 1 lớp", unit: "m²", price: 320000, category: "thachcao" },
            { code: "AD.11114", name: "Làm vách ngăn thạch cao 2 lớp", unit: "m²", price: 420000, category: "thachcao" },
            { code: "AD.11115", name: "Làm hộp kỹ thuật thạch cao", unit: "m", price: 180000, category: "thachcao" },
            
            // Đồ gỗ nội thất
            { code: "AD.21111", name: "Lắp đặt tủ bếp gỗ công nghiệp", unit: "m", price: 3200000, category: "do" },
            { code: "AD.21112", name: "Lắp đặt tủ quần áo gỗ công nghiệp", unit: "m²", price: 2800000, category: "do" },
            { code: "AD.21113", name: "Lắp đặt kệ tivi gỗ công nghiệp", unit: "bộ", price: 4500000, category: "do" },
            { code: "AD.21114", name: "Lắp đặt giường ngủ gỗ công nghiệp", unit: "cái", price: 5500000, category: "do" },
            { code: "AD.21115", name: "Lắp đặt bàn làm việc gỗ công nghiệp", unit: "cái", price: 3800000, category: "do" },
            
            // Cửa các loại
            { code: "AD.31111", name: "Lắp đặt cửa đi gỗ công nghiệp", unit: "bộ", price: 3200000, category: "cua" },
            { code: "AD.31112", name: "Lắp đặt cửa đi gỗ tự nhiên", unit: "bộ", price: 4800000, category: "cua" },
            { code: "AD.31113", name: "Lắp đặt cửa sổ nhôm kính", unit: "m²", price: 1600000, category: "cua" },
            { code: "AD.31114", name: "Lắp đặt cửa đi nhôm kính", unit: "m²", price: 1800000, category: "cua" },
            { code: "AD.31115", name: "Lắp đặt cửa cuốn", unit: "m²", price: 1500000, category: "cua" },
            { code: "AD.31116", name: "Lắp đặt cửa nhựa lõi thép", unit: "bộ", price: 2800000, category: "cua" },
            
            // Thiết bị bếp
            { code: "AD.41111", name: "Lắp đặt bếp gas âm", unit: "cái", price: 650000, category: "bep" },
            { code: "AD.41112", name: "Lắp đặt bếp từ", unit: "cái", price: 850000, category: "bep" },
            { code: "AD.41113", name: "Lắp đặt máy hút mùi", unit: "cái", price: 750000, category: "bep" },
            { code: "AD.41114", name: "Lắp đặt chậu rửa bát", unit: "cái", price: 480000, category: "bep" },
            { code: "AD.41115", name: "Lắp đặt vòi rửa bát", unit: "cái", price: 380000, category: "bep" }
        ];

        // Material definitions
        const materialDefinitions = {
            // Xi măng
            "ximang-pcb30": { name: "Xi măng PCB30", unit: "bao", price: 85000, category: "ximang" },
            "ximang-pcb40": { name: "Xi măng PCB40", unit: "bao", price: 95000, category: "ximang" },
            
            // Cát
            "cat-den": { name: "Cát đen", unit: "m³", price: 350000, category: "cat" },
            "cat-vang": { name: "Cát vàng", unit: "m³", price: 420000, category: "cat" },
            "cat-san-lap": { name: "Cát san lấp", unit: "m³", price: 180000, category: "cat" },
            
            // Gạch
            "gach-dac": { name: "Gạch đặc 6.5x10.5x22", unit: "viên", price: 2000, category: "gach" },
            "gach-hai-lo": { name: "Gạch hai lỗ 8x8x18", unit: "viên", price: 1800, category: "gach" },
            "gach-ceramic-30x30": { name: "Gạch ceramic 30x30", unit: "m²", price: 150000, category: "gach" },
            "gach-ceramic-40x40": { name: "Gạch ceramic 40x40", unit: "m²", price: 170000, category: "gach" },
            "gach-granite-60x60": { name: "Gạch granite 60x60", unit: "m²", price: 280000, category: "gach" },
            "gach-op-tuong-30x60": { name: "Gạch ốp tường 30x60", unit: "m²", price: 170000, category: "gach" },
            
            // Đá
            "da-1x2": { name: "Đá 1x2", unit: "m³", price: 380000, category: "khac" },
            "da-2x4": { name: "Đá 2x4", unit: "m³", price: 350000, category: "khac" },
            "da-4x6": { name: "Đá 4x6", unit: "m³", price: 330000, category: "khac" },
            
            // Thép
            "thep-phi-6": { name: "Thép phi 6", unit: "kg", price: 23000, category: "khac" },
            "thep-phi-8": { name: "Thép phi 8", unit: "kg", price: 23000, category: "khac" },
            "thep-phi-10": { name: "Thép phi 10", unit: "kg", price: 23000, category: "khac" },
            "thep-phi-12": { name: "Thép phi 12", unit: "kg", price: 23000, category: "khac" },
            "thep-phi-14": { name: "Thép phi 14", unit: "kg", price: 23000, category: "khac" },
            "thep-phi-16": { name: "Thép phi 16", unit: "kg", price: 23000, category: "khac" },
            "thep-phi-18": { name: "Thép phi 18", unit: "kg", price: 23000, category: "khac" },
            "day-thep-buoc": { name: "Dây thép buộc", unit: "kg", price: 25000, category: "khac" },
            
            // Vật tư khác
            "go-coffa": { name: "Gỗ coffa", unit: "m²", price: 35000, category: "khac" },
            "dinh": { name: "Đinh các loại", unit: "kg", price: 25000, category: "khac" },
            "son-nuoc": { name: "Sơn nước", unit: "kg", price: 70000, category: "khac" },
            "son-dau": { name: "Sơn dầu", unit: "kg", price: 85000, category: "khac" },
            "matit": { name: "Bột bả matit", unit: "kg", price: 15000, category: "khac" },
            "keo-dan-gach": { name: "Keo dán gạch", unit: "bao", price: 120000, category: "khac" },
            "keo-chi-ron": { name: "Keo chỉ ron", unit: "kg", price: 35000, category: "khac" },
            "tam-thach-cao": { name: "Tấm thạch cao", unit: "m²", price: 65000, category: "khac" },
            "khung-thach-cao": { name: "Khung xương thạch cao", unit: "m²", price: 55000, category: "khac" },
            "ton-ma-kem": { name: "Tôn mạ kẽm", unit: "m²", price: 120000, category: "khac" },
            "ton-ma-mau": { name: "Tôn mạ màu", unit: "m²", price: 150000, category: "khac" },
            "ngoi-dat-nung": { name: "Ngói đất nung", unit: "viên", price: 5000, category: "khac" },
            "xa-go-thep": { name: "Xà gồ thép", unit: "m", price: 75000, category: "khac" },
            "day-dien-2x1.5": { name: "Dây điện 2x1.5", unit: "m", price: 12000, category: "khac" },
            "day-dien-2x2.5": { name: "Dây điện 2x2.5", unit: "m", price: 18000, category: "khac" },
            "day-dien-2x4": { name: "Dây điện 2x4", unit: "m", price: 28000, category: "khac" },
            "ong-ruot-ga": { name: "Ống ruột gà", unit: "m", price: 8000, category: "khac" },
            "o-cam-don": { name: "Ổ cắm đơn", unit: "cái", price: 35000, category: "khac" },
            "o-cam-doi": { name: "Ổ cắm đôi", unit: "cái", price: 45000, category: "khac" },
            "cong-tac-don": { name: "Công tắc đơn", unit: "cái", price: 30000, category: "khac" },
            "cong-tac-doi": { name: "Công tắc đôi", unit: "cái", price: 40000, category: "khac" },
            "den-downlight": { name: "Đèn downlight", unit: "cái", price: 65000, category: "khac" },
            "den-led-am-tran": { name: "Đèn led âm trần", unit: "cái", price: 85000, category: "khac" },
            "ong-nuoc-ppr-21": { name: "Ống nước PPR 21", unit: "m", price: 25000, category: "khac" },
            "ong-nuoc-ppr-27": { name: "Ống nước PPR 27", unit: "m", price: 35000, category: "khac" },
            "ong-thoat-pvc-60": { name: "Ống thoát PVC 60", unit: "m", price: 30000, category: "khac" },
            "ong-thoat-pvc-90": { name: "Ống thoát PVC 90", unit: "m", price: 45000, category: "khac" },
            "ong-thoat-pvc-114": { name: "Ống thoát PVC 114", unit: "m", price: 65000, category: "khac" },
            "van-khoa-nuoc": { name: "Van khóa nước", unit: "cái", price: 45000, category: "khac" },
            "bon-cau": { name: "Bồn cầu", unit: "bộ", price: 2500000, category: "khac" },
            "lavabo": { name: "Lavabo", unit: "bộ", price: 1500000, category: "khac" },
            "voi-sen": { name: "Vòi sen", unit: "bộ", price: 850000, category: "khac" },
            "voi-rua": { name: "Vòi rửa", unit: "cái", price: 450000, category: "khac" },
            "guong-phong-tam": { name: "Gương phòng tắm", unit: "cái", price: 350000, category: "khac" },
            "phu-kien-phong-tam": { name: "Phụ kiện phòng tắm", unit: "bộ", price: 650000, category: "khac" },
            "go-cong-nghiep": { name: "Gỗ công nghiệp", unit: "m²", price: 320000, category: "khac" },
            "kinh": { name: "Kính", unit: "m²", price: 280000, category: "khac" },
            "thanh-nhom": { name: "Thanh nhôm", unit: "m", price: 120000, category: "khac" }
        };

        // Material quantities for work items
        const materialQuantities = {
            // Công tác đất
            "AB.11111": {}, // Đào đất hố móng công trình - Không có vật tư
            "AB.11112": {}, // Đào đất hố móng bằng máy đào - Không có vật tư
            "AB.11113": { "cat-san-lap": 1.1 }, // Đắp đất nền công trình - 1.1 m³ cát/m³ đất đắp
            "AB.11114": {}, // Vận chuyển đất đi đổ - Không có vật tư
            "AB.11115": {}, // San nền bằng thủ công - Không có vật tư
            
            // Công tác móng
            "AB.21111": { "ximang-pcb40": 7.5, "cat-vang": 0.57, "da-1x2": 0.87, "thep-phi-10": 25 }, // Làm móng đơn BTCT
            "AB.21112": { "ximang-pcb40": 7.2, "cat-vang": 0.55, "da-1x2": 0.85, "thep-phi-10": 23 }, // Làm móng băng BTCT
            "AB.21113": { "ximang-pcb40": 7.4, "cat-vang": 0.56, "da-1x2": 0.86, "thep-phi-10": 22 }, // Làm móng bè BTCT
            "AB.21114": {}, // Đóng cọc bê tông - Không tính vật tư
            "AB.21115": { "ximang-pcb30": 5.0, "cat-vang": 0.60, "da-1x2": 0.90 }, // Đổ bê tông lót móng M100
            
            // Công tác bê tông
            "AB.31111": { "ximang-pcb40": 7.8, "cat-vang": 0.58, "da-1x2": 0.88, "thep-phi-12": 28 }, // Đổ bê tông cột M250
            "AB.31112": { "ximang-pcb40": 7.6, "cat-vang": 0.56, "da-1x2": 0.86, "thep-phi-12": 25 }, // Đổ bê tông dầm M250
            "AB.31113": { "ximang-pcb40": 7.5, "cat-vang": 0.56, "da-1x2": 0.86, "thep-phi-10": 22 }, // Đổ bê tông sàn M250
            "AB.31114": { "ximang-pcb40": 7.5, "cat-vang": 0.57, "da-1x2": 0.87, "thep-phi-10": 25 }, // Đổ bê tông móng M250
            "AB.31115": { "go-coffa": 1.1, "dinh": 0.1 }, // Làm coffa cột
            "AB.31116": { "go-coffa": 1.1, "dinh": 0.1 }, // Làm coffa dầm
            "AB.31117": { "go-coffa": 1.1, "dinh": 0.08 }, // Làm coffa sàn
            "AB.31118": { "day-thep-buoc": 0.02 }, // Gia công lắp đặt thép
            
            // Công tác xây
            "AB.41111": { "gach-dac": 70, "ximang-pcb30": 0.5, "cat-vang": 0.04 }, // Xây tường gạch đặc 100mm
            "AB.41112": { "gach-dac": 140, "ximang-pcb30": 0.7, "cat-vang": 0.06 }, // Xây tường gạch đặc 200mm
            "AB.41113": { "gach-hai-lo": 65, "ximang-pcb30": 0.4, "cat-vang": 0.03 }, // Xây tường gạch hai lỗ 100mm
            "AB.41114": { "gach-hai-lo": 130, "ximang-pcb30": 0.6, "cat-vang": 0.05 }, // Xây tường gạch hai lỗ 200mm
            "AB.41115": { "ximang-pcb30": 0.3, "cat-vang": 0.03 }, // Xây tường gạch block - Vật tư chính
            
            // Công tác trát
            "AB.51111": { "ximang-pcb30": 0.3, "cat-vang": 0.018 }, // Trát tường trong nhà dày 15mm
            "AB.51112": { "ximang-pcb30": 0.35, "cat-vang": 0.022 }, // Trát tường ngoài nhà dày 20mm
            "AB.51113": { "ximang-pcb30": 0.3, "cat-vang": 0.018 }, // Trát trần dày 15mm
            "AB.51114": { "ximang-pcb30": 0.3, "cat-vang": 0.018 }, // Trát cột dày 15mm
            
            // Công tác lát gạch
            "AB.61111": { "gach-ceramic-30x30": 1.05, "keo-dan-gach": 0.3, "keo-chi-ron": 0.15 }, // Lát gạch ceramic 30x30cm nền
            "AB.61112": { "gach-ceramic-40x40": 1.05, "keo-dan-gach": 0.3, "keo-chi-ron": 0.12 }, // Lát gạch ceramic 40x40cm nền
            "AB.61113": { "gach-granite-60x60": 1.05, "keo-dan-gach": 0.35, "keo-chi-ron": 0.1 }, // Lát gạch granite 60x60cm nền
            "AB.61114": { "gach-op-tuong-30x60": 1.05, "keo-dan-gach": 0.4, "keo-chi-ron": 0.15 }, // Ốp gạch ceramic 30x60cm tường
            "AB.61115": { "keo-dan-gach": 0.35, "keo-chi-ron": 0.18 }, // Ốp gạch ceramic 25x40cm tường
            
            // Công tác sơn
            "AB.71111": { "son-nuoc": 0.3, "matit": 0.2 }, // Sơn nước trong nhà 3 nước
            "AB.71112": { "son-nuoc": 0.35, "matit": 0.22 }, // Sơn nước ngoài nhà 3 nước
            "AB.71113": { "matit": 0.5 }, // Bả matit tường trong nhà
            "AB.71114": { "matit": 0.55 }, // Bả matit tường ngoài nhà
            "AB.71115": { "son-dau": 0.25 }, // Sơn dầu cửa gỗ
            
            // Công tác mái
            "AB.81111": { "ngoi-dat-nung": 18, "ximang-pcb30": 0.2, "cat-vang": 0.01 }, // Lợp mái ngói đất nung
            "AB.81112": { "ton-ma-kem": 1.05, "xa-go-thep": 2 }, // Lợp mái tôn lạnh mạ kẽm
            "AB.81113": { "ton-ma-mau": 1.05, "xa-go-thep": 2 }, // Lợp mái tôn mạ màu
            "AB.81114": { "ximang-pcb40": 7.5, "cat-vang": 0.56, "da-1x2": 0.86, "thep-phi-10": 22 }, // Đổ mái BTCT dày 10cm
            "AB.81115": {}, // Chống thấm mái - Vật tư được tính riêng
            
            // Hệ thống điện
            "AB.11111": { "day-dien-2x1.5": 1.02 }, // Đi dây điện trong tường
            "AB.11112": { "day-dien-2x1.5": 1.02, "ong-ruot-ga": 1.02 }, // Đi dây điện trong ống ruột gà
            "AB.11113": { "o-cam-don": 1 }, // Lắp đặt ổ cắm đơn
            "AB.11114": { "o-cam-doi": 1 }, // Lắp đặt ổ cắm đôi
            "AB.11115": { "cong-tac-don": 1 }, // Lắp đặt công tắc đơn
            "AB.11116": { "cong-tac-doi": 1 }, // Lắp đặt công tắc đôi
            "AB.11117": { "den-downlight": 1 }, // Lắp đặt đèn downlight
            "AB.11118": { "den-led-am-tran": 1 }, // Lắp đặt đèn led âm trần
        };

        // Sample estimate data
        let estimateData = [
            { code: "AB.41111", name: "Xây tường gạch đặc 100mm", unit: "m²", quantity: 85, price: 320000 },
            { code: "AB.61111", name: "Lát gạch ceramic 30x30cm nền", unit: "m²", quantity: 45, price: 280000 },
            { code: "AB.71111", name: "Sơn nước trong nhà 3 nước", unit: "m²", quantity: 120, price: 75000 },
            { code: "AD.31111", name: "Lắp đặt cửa đi gỗ công nghiệp", unit: "bộ", quantity: 4, price: 3200000 }
        ];

        // DOM elements
        const tabs = document.querySelectorAll('.tab-button');
        const tabContents = document.querySelectorAll('.tab-content');
        const estimateTableBody = document.getElementById('estimateTableBody');
        const materialsTableBody = document.getElementById('materialsTableBody');
        const totalAmount = document.getElementById('totalAmount');
        const totalMaterialAmount = document.getElementById('totalMaterialAmount');
        const addWorkBtn = document.getElementById('addWorkBtn');
        const addWorkModal = document.getElementById('addWorkModal');
        const closeModalBtns = document.querySelectorAll('.close-modal');
        const workCategory = document.getElementById('workCategory');
        const workSearch = document.getElementById('workSearch');
        const searchResults = document.getElementById('searchResults');
        const selectedWorkInfo = document.getElementById('selectedWorkInfo');
        const workQuantity = document.getElementById('workQuantity');
        const addWorkToEstimateBtn = document.getElementById('addWorkToEstimateBtn');
        const notification = document.getElementById('notification');
        const notificationMessage = document.getElementById('notificationMessage');
        const materialFilter = document.getElementById('materialFilter');
        const exportExcelBtn = document.getElementById('exportExcelBtn');
        const exportMaterialsBtn = document.getElementById('exportMaterialsBtn');

        // Charts
        let costDistributionChart;
        let top10MaterialsChart;

        // Selected work in modal
        let selectedWork = null;

        // Initialize
        document.addEventListener('DOMContentLoaded', function() {
            // Initialize tables
            renderEstimateTable();
            renderMaterialsTable();
            
            // Initialize charts
            initializeCharts();
            
            // Tab switching
            tabs.forEach(tab => {
                tab.addEventListener('click', function() {
                    const tabId = this.getAttribute('data-tab');
                    
                    // Remove active class from all tabs
                    tabs.forEach(tab => tab.classList.remove('tab-active'));
                    tabContents.forEach(content => content.classList.add('hidden'));
                    
                    // Add active class to current tab
                    this.classList.add('tab-active');
                    document.getElementById(`${tabId}-tab`).classList.remove('hidden');
                    
                    // Update charts if on biểu đồ tab
                    if (tabId === 'bieudo') {
                        updateCharts();
                    }
                });
            });
            
            // Add Work Modal
            addWorkBtn.addEventListener('click', openAddWorkModal);
            closeModalBtns.forEach(btn => {
                btn.addEventListener('click', closeAddWorkModal);
            });
            
            // Work Search
            workSearch.addEventListener('input', searchWork);
            workCategory.addEventListener('change', searchWork);
            
            // Add Work to Estimate
            addWorkToEstimateBtn.addEventListener('click', addWorkToEstimate);
            
            // Material Filter
            materialFilter.addEventListener('change', function() {
                renderMaterialsTable();
            });
            
            // Export Excel
            exportExcelBtn.addEventListener('click', exportEstimateToExcel);
            exportMaterialsBtn.addEventListener('click', exportMaterialsToExcel);
        });

        // Render Estimate Table
        function renderEstimateTable() {
            estimateTableBody.innerHTML = '';
            
            estimateData.forEach((item, index) => {
                const row = document.createElement('tr');
                const total = item.quantity * item.price;
                
                row.innerHTML = `
                    <td>${index + 1}</td>
                    <td>${item.code}</td>
                    <td>${item.name}</td>
                    <td>${item.unit}</td>
                    <td class="editable text-right" data-type="quantity" data-index="${index}">${item.quantity}</td>
                    <td class="editable text-right" data-type="price" data-index="${index}">${formatCurrency(item.price)}</td>
                    <td class="text-right">${formatCurrency(total)}</td>
                    <td>
                        <button class="text-red-500 delete-work" data-index="${index}">
                            <i class="fas fa-trash-alt"></i>
                        </button>
                    </td>
                `;
                
                estimateTableBody.appendChild(row);
            });
            
            // Add event listeners to editable cells
            document.querySelectorAll('.editable').forEach(cell => {
                cell.addEventListener('click', editCell);
            });
            
            // Add event listeners to delete buttons
            document.querySelectorAll('.delete-work').forEach(btn => {
                btn.addEventListener('click', deleteWork);
            });
            
            // Update total
            updateTotal();
        }

        // Edit Cell
        function editCell() {
            const cell = this;
            const type = cell.getAttribute('data-type');
            const index = parseInt(cell.getAttribute('data-index'));
            const item = estimateData[index];
            
            let value = type === 'quantity' ? item.quantity : item.price;
            
            // Create input element
            const input = document.createElement('input');
            input.type = 'text';
            input.value = value;
            input.className = 'w-full p-1 border border-blue-500 rounded-sm';
            
            // Replace cell content with input
            cell.innerHTML = '';
            cell.appendChild(input);
            input.focus();
            
            // Handle input blur
            input.addEventListener('blur', function() {
                finishEditing(cell, input, type, index);
            });
            
            // Handle input enter key
            input.addEventListener('keypress', function(e) {
                if (e.key === 'Enter') {
                    finishEditing(cell, input, type, index);
                }
            });
        }

        // Finish Editing
        function finishEditing(cell, input, type, index) {
            let value = input.value;
            
            // Parse number value
            if (type === 'price') {
                value = value.replace(/\D/g, '');
            }
            
            value = parseFloat(value);
            
            if (isNaN(value) || value <= 0) {
                showNotification('Giá trị không hợp lệ', 'error');
                
                // Restore original value
                const item = estimateData[index];
                value = type === 'quantity' ? item.quantity : item.price;
            }
            
            // Update data
            if (type === 'quantity') {
                estimateData[index].quantity = value;
                cell.textContent = value;
            } else {
                estimateData[index].price = value;
                cell.textContent = formatCurrency(value);
            }
            
            // Update row total
            const row = cell.parentNode;
            const totalCell = row.cells[6];
            const total = estimateData[index].quantity * estimateData[index].price;
            totalCell.textContent = formatCurrency(total);
            
            // Update total and materials
            updateTotal();
            renderMaterialsTable();
            updateCharts();
        }

        // Delete Work
        function deleteWork() {
            const index = parseInt(this.getAttribute('data-index'));
            
            // Remove item from data
            estimateData.splice(index, 1);
            
            // Re-render table
            renderEstimateTable();
            renderMaterialsTable();
            updateCharts();
            
            showNotification('Đã xóa công việc', 'success');
        }

        // Update Total
        function updateTotal() {
            let total = 0;
            
            estimateData.forEach(item => {
                total += item.quantity * item.price;
            });
            
            totalAmount.textContent = formatCurrency(total);
        }

        // Render Materials Table
        function renderMaterialsTable() {
            materialsTableBody.innerHTML = '';
            
            const materials = calculateMaterials();
            const filter = materialFilter.value;
            
            let filteredMaterials = materials;
            if (filter !== 'all') {
                filteredMaterials = materials.filter(m => m.category === filter);
            }
            
            filteredMaterials.forEach((material, index) => {
                const row = document.createElement('tr');
                
                let categoryBadge = '';
                switch (material.category) {
                    case 'ximang':
                        categoryBadge = '<span class="material-badge badge-ximang">Xi măng</span>';
                        break;
                    case 'cat':
                        categoryBadge = '<span class="material-badge badge-cat">Cát</span>';
                        break;
                    case 'gach':
                        categoryBadge = '<span class="material-badge badge-gach">Gạch</span>';
                        break;
                    default:
                        categoryBadge = '<span class="material-badge badge-khac">Khác</span>';
                }
                
                row.innerHTML = `
                    <td>${index + 1}</td>
                    <td>${categoryBadge}</td>
                    <td>${material.name}</td>
                    <td>${material.unit}</td>
                    <td class="text-right">${material.quantity.toFixed(2)}</td>
                    <td class="editable text-right" data-type="material-price" data-id="${material.id}">${formatCurrency(material.price)}</td>
                    <td class="text-right">${formatCurrency(material.total)}</td>
                `;
                
                materialsTableBody.appendChild(row);
            });
            
            // Add event listeners to editable cells
            document.querySelectorAll('[data-type="material-price"]').forEach(cell => {
                cell.addEventListener('click', editMaterialPrice);
            });
            
            // Update total material amount
            updateTotalMaterialAmount(materials);
        }

        // Calculate Materials
        function calculateMaterials() {
            const materialQuantitiesMap = {};
            
            // Calculate quantities from work items
            estimateData.forEach(item => {
                const workMaterials = materialQuantities[item.code] || {};
                
                for (const materialId in workMaterials) {
                    const quantityPerUnit = workMaterials[materialId];
                    const totalQuantity = quantityPerUnit * item.quantity;
                    
                    if (!materialQuantitiesMap[materialId]) {
                        const materialDef = materialDefinitions[materialId];
                        materialQuantitiesMap[materialId] = {
                            id: materialId,
                            name: materialDef.name,
                            unit: materialDef.unit,
                            quantity: 0,
                            price: materialDef.price,
                            category: materialDef.category
                        };
                    }
                    
                    materialQuantitiesMap[materialId].quantity += totalQuantity;
                }
            });
            
            // Convert to array and calculate totals
            const materials = Object.values(materialQuantitiesMap);
            materials.forEach(material => {
                material.total = material.quantity * material.price;
            });
            
            // Sort by category and then by total (descending)
            return materials.sort((a, b) => {
                if (a.category !== b.category) {
                    return a.category.localeCompare(b.category);
                }
                return b.total - a.total;
            });
        }

        // Edit Material Price
        function editMaterialPrice() {
            const cell = this;
            const materialId = cell.getAttribute('data-id');
            
            // Create input element
            const input = document.createElement('input');
            input.type = 'text';
            input.value = materialDefinitions[materialId].price;
            input.className = 'w-full p-1 border border-blue-500 rounded-sm';
            
            // Replace cell content with input
            cell.innerHTML = '';
            cell.appendChild(input);
            input.focus();
            
            // Handle input blur
            input.addEventListener('blur', function() {
                finishEditingMaterialPrice(cell, input, materialId);
            });
            
            // Handle input enter key
            input.addEventListener('keypress', function(e) {
                if (e.key === 'Enter') {
                    finishEditingMaterialPrice(cell, input, materialId);
                }
            });
        }

        // Finish Editing Material Price
        function finishEditingMaterialPrice(cell, input, materialId) {
            let value = input.value.replace(/\D/g, '');
            value = parseInt(value);
            
            if (isNaN(value) || value <= 0) {
                showNotification('Giá trị không hợp lệ', 'error');
                value = materialDefinitions[materialId].price;
            }
            
            // Update material definition
            materialDefinitions[materialId].price = value;
            
            // Update UI
            cell.textContent = formatCurrency(value);
            
            // Re-render materials table
            renderMaterialsTable();
            updateCharts();
            
            showNotification('Đã cập nhật đơn giá vật tư', 'success');
        }

        // Update Total Material Amount
        function updateTotalMaterialAmount(materials) {
            let total = 0;
            
            materials.forEach(material => {
                total += material.total;
            });
            
            totalMaterialAmount.textContent = formatCurrency(total);
        }

        // Initialize Charts
        function initializeCharts() {
            const costDistributionCtx = document.getElementById('costDistributionChart').getContext('2d');
            const top10MaterialsCtx = document.getElementById('top10MaterialsChart').getContext('2d');
            
            // Cost Distribution Chart
            costDistributionChart = new Chart(costDistributionCtx, {
                type: 'pie',
                data: {
                    labels: ['Xi măng', 'Cát', 'Gạch', 'Khác'],
                    datasets: [{
                        data: [25, 15, 20, 40],
                        backgroundColor: ['#3b82f6', '#ef4444', '#f59e0b', '#6b7280'],
                        borderWidth: 1
                    }]
                },
                options: {
                    responsive: true,
                    maintainAspectRatio: false,
                    plugins: {
                        legend: {
                            position: 'bottom'
                        },
                        tooltip: {
                            callbacks: {
                                label: function(context) {
                                    const label = context.label || '';
                                    const value = context.parsed || 0;
                                    const total = context.dataset.data.reduce((a, b) => a + b, 0);
                                    const percentage = Math.round((value / total) * 100);
                                    return `${label}: ${percentage}% (${formatCurrency(value)})`;
                                }
                            }
                        }
                    }
                }
            });
            
            // Top 10 Materials Chart
            top10MaterialsChart = new Chart(top10MaterialsCtx, {
                type: 'bar',
                data: {
                    labels: ['Gạch ceramic 30x30', 'Xi măng PCB40', 'Cát vàng', 'Keo chỉ ron', 'Thép phi 10', 'Đá 1x2', 'Sơn nước', 'Tấm thạch cao', 'Gạch ốp tường', 'Gỗ công nghiệp'],
                    datasets: [{
                        label: 'Chi phí (VNĐ)',
                        data: [12000000, 8500000, 6200000, 3500000, 3200000, 2800000, 2500000, 2200000, 2000000, 1800000],
                        backgroundColor: '#3b82f6',
                        borderWidth: 1
                    }]
                },
                options: {
                    indexAxis: 'y',
                    responsive: true,
                    maintainAspectRatio: false,
                    plugins: {
                        legend: {
                            display: false
                        },
                        tooltip: {
                            callbacks: {
                                label: function(context) {
                                    return `Chi phí: ${formatCurrency(context.parsed.x)}`;
                                }
                            }
                        }
                    },
                    scales: {
                        x: {
                            beginAtZero: true,
                            ticks: {
                                callback: function(value) {
                                    return formatCompactCurrency(value);
                                }
                            }
                        }
                    }
                }
            });
        }

        // Update Charts
        function updateCharts() {
            const materials = calculateMaterials();
            
            // Calculate costs by category
            const categoryTotals = {
                ximang: 0,
                cat: 0,
                gach: 0,
                khac: 0
            };
            
            materials.forEach(material => {
                categoryTotals[material.category] += material.total;
            });
            
            // Update cost distribution chart
            costDistributionChart.data.datasets[0].data = [
                categoryTotals.ximang,
                categoryTotals.cat,
                categoryTotals.gach,
                categoryTotals.khac
            ];
            costDistributionChart.update();
            
            // Sort materials by total cost and get top 10
            const top10 = [...materials].sort((a, b) => b.total - a.total).slice(0, 10);
            
            // Update top 10 materials chart
            top10MaterialsChart.data.labels = top10.map(m => m.name);
            top10MaterialsChart.data.datasets[0].data = top10.map(m => m.total);
            top10MaterialsChart.update();
        }

        // Open Add Work Modal
        function openAddWorkModal() {
            addWorkModal.classList.add('active');
            workSearch.value = '';
            workCategory.value = 'all';
            workQuantity.value = '';
            selectedWork = null;
            selectedWorkInfo.classList.add('hidden');
            searchResults.classList.add('hidden');
        }

        // Close Add Work Modal
        function closeAddWorkModal() {
            addWorkModal.classList.remove('active');
        }

        // Search Work
        function searchWork() {
            const searchTerm = workSearch.value.toLowerCase();
            const categoryFilter = workCategory.value;
            
            if (searchTerm.length < 2 && categoryFilter === 'all') {
                searchResults.classList.add('hidden');
                return;
            }
            
            // Filter work items
            const filtered = workItems.filter(item => {
                const matchesCategory = categoryFilter === 'all' || item.category === categoryFilter;
                const matchesSearch = searchTerm.length < 2 || 
                    item.code.toLowerCase().includes(searchTerm) || 
                    item.name.toLowerCase().includes(searchTerm);
                
                return matchesCategory && matchesSearch;
            });
            
            // Display results
            searchResults.innerHTML = '';
            
            if (filtered.length === 0) {
                searchResults.innerHTML = '<div class="p-3 text-gray-500">Không tìm thấy kết quả</div>';
                searchResults.classList.remove('hidden');
                return;
            }
            
            filtered.forEach(item => {
                const resultItem = document.createElement('div');
                resultItem.className = 'search-result-item';
                resultItem.innerHTML = `
                    <div class="font-medium">${item.name}</div>
                    <div class="text-sm text-gray-600">
                        <span>${item.code}</span>
                        <span class="mx-2">|</span>
                        <span>${item.unit}</span>
                        <span class="mx-2">|</span>
                        <span>${formatCurrency(item.price)}</span>
                    </div>
                `;
                
                resultItem.addEventListener('click', function() {
                    selectWork(item);
                });
                
                searchResults.appendChild(resultItem);
            });
            
            searchResults.classList.remove('hidden');
        }

        // Select Work
        function selectWork(work) {
            selectedWork = work;
            
            // Update UI
            document.getElementById('selectedWorkName').textContent = work.name;
            document.getElementById('selectedWorkCode').textContent = `Mã hiệu: ${work.code}`;
            document.getElementById('selectedWorkUnit').textContent = `Đơn vị: ${work.unit}`;
            document.getElementById('selectedWorkPrice').textContent = `Đơn giá: ${formatCurrency(work.price)}`;
            
            selectedWorkInfo.classList.remove('hidden');
            searchResults.classList.add('hidden');
            workSearch.value = work.name;
            workQuantity.focus();
        }

        // Add Work to Estimate
        function addWorkToEstimate() {
            if (!selectedWork) {
                showNotification('Vui lòng chọn công việc', 'error');
                return;
            }
            
            const quantity = parseFloat(workQuantity.value);
            
            if (isNaN(quantity) || quantity <= 0) {
                showNotification('Vui lòng nhập khối lượng hợp lệ', 'error');
                return;
            }
            
            // Add to estimate data
            estimateData.push({
                code: selectedWork.code,
                name: selectedWork.name,
                unit: selectedWork.unit,
                quantity: quantity,
                price: selectedWork.price
            });
            
            // Update UI
            renderEstimateTable();
            renderMaterialsTable();
            updateCharts();
            
            // Close modal
            closeAddWorkModal();
            
            showNotification('Đã thêm công việc vào dự toán', 'success');
        }

        // Export Estimate to Excel
        function exportEstimateToExcel() {
            const projectName = document.getElementById('projectName').value || 'Dự toán';
            const projectLocation = document.getElementById('projectLocation').value || '';
            
            // Create workbook
            const wb = XLSX.utils.book_new();
            
            // Create estimate worksheet
            const estimateWsData = [
                ['DỰ TOÁN CHI TIẾT'],
                ['Công ty TNHH Thiết kế và xây dựng VTZ Spaxe'],
                [''],
                ['Dự án: ' + projectName],
                ['Địa điểm: ' + projectLocation],
                ['Ngày lập: ' + new Date().toLocaleDateString('vi-VN')],
                [''],
                ['STT', 'Mã hiệu', 'Tên công việc', 'Đơn vị', 'Khối lượng', 'Đơn giá (VNĐ)', 'Thành tiền (VNĐ)']
            ];
            
            let totalEstimate = 0;
            
            // Add estimate data
            estimateData.forEach((item, index) => {
                const total = item.quantity * item.price;
                totalEstimate += total;
                
                estimateWsData.push([
                    index + 1,
                    item.code,
                    item.name,
                    item.unit,
                    item.quantity,
                    item.price,
                    total
                ]);
            });
            
            // Add total row
            estimateWsData.push(['', '', '', '', '', 'Tổng cộng:', totalEstimate]);
            
            const estimateWs = XLSX.utils.aoa_to_sheet(estimateWsData);
            XLSX.utils.book_append_sheet(wb, estimateWs, 'Dự toán');
            
            // Create materials worksheet
            const materials = calculateMaterials();
            
            const materialsWsData = [
                ['BẢNG VẬT TƯ TỔNG HỢP'],
                ['Công ty TNHH Thiết kế và xây dựng VTZ Spaxe'],
                [''],
                ['Dự án: ' + projectName],
                ['Ngày lập: ' + new Date().toLocaleDateString('vi-VN')],
                [''],
                ['STT', 'Nhóm vật tư', 'Tên vật tư', 'Đơn vị', 'Khối lượng', 'Đơn giá (VNĐ)', 'Thành tiền (VNĐ)']
            ];
            
            let totalMaterials = 0;
            
            // Add materials data
            materials.forEach((material, index) => {
                const categoryName = {
                    'ximang': 'Xi măng',
                    'cat': 'Cát',
                    'gach': 'Gạch',
                    'khac': 'Khác'
                }[material.category] || 'Khác';
                
                totalMaterials += material.total;
                
                materialsWsData.push([
                    index + 1,
                    categoryName,
                    material.name,
                    material.unit,
                    material.quantity,
                    material.price,
                    material.total
                ]);
            });
            
            // Add total row
            materialsWsData.push(['', '', '', '', '', 'Tổng cộng:', totalMaterials]);
            
            const materialsWs = XLSX.utils.aoa_to_sheet(materialsWsData);
            XLSX.utils.book_append_sheet(wb, materialsWs, 'Vật tư');
            
            // Generate Excel file
            XLSX.writeFile(wb, `${projectName}_Dự toán.xlsx`);
            
            showNotification('Đã xuất dự toán ra Excel', 'success');
        }

        // Export Materials to Excel
        function exportMaterialsToExcel() {
            const projectName = document.getElementById('projectName').value || 'Dự toán';
            
            // Create workbook
            const wb = XLSX.utils.book_new();
            
            // Create materials worksheet
            const materials = calculateMaterials();
            const filter = materialFilter.value;
            
            let filteredMaterials = materials;
            let filterName = 'Tất cả vật tư';
            
            if (filter !== 'all') {
                filteredMaterials = materials.filter(m => m.category === filter);
                filterName = {
                    'ximang': 'Xi măng',
                    'cat': 'Cát',
                    'gach': 'Gạch',
                    'khac': 'Khác'
                }[filter] || 'Tất cả vật tư';
            }
            
            const materialsWsData = [
                ['BẢNG VẬT TƯ TỔNG HỢP - ' + filterName.toUpperCase()],
                ['Công ty TNHH Thiết kế và xây dựng VTZ Spaxe'],
                [''],
                ['Dự án: ' + projectName],
                ['Ngày lập: ' + new Date().toLocaleDateString('vi-VN')],
                [''],
                ['STT', 'Nhóm vật tư', 'Tên vật tư', 'Đơn vị', 'Khối lượng', 'Đơn giá (VNĐ)', 'Thành tiền (VNĐ)']
            ];
            
            let totalMaterials = 0;
            
            // Add materials data
            filteredMaterials.forEach((material, index) => {
                const categoryName = {
                    'ximang': 'Xi măng',
                    'cat': 'Cát',
                    'gach': 'Gạch',
                    'khac': 'Khác'
                }[material.category] || 'Khác';
                
                totalMaterials += material.total;
                
                materialsWsData.push([
                    index + 1,
                    categoryName,
                    material.name,
                    material.unit,
                    material.quantity,
                    material.price,
                    material.total
                ]);
            });
            
            // Add total row
            materialsWsData.push(['', '', '', '', '', 'Tổng cộng:', totalMaterials]);
            
            const materialsWs = XLSX.utils.aoa_to_sheet(materialsWsData);
            XLSX.utils.book_append_sheet(wb, materialsWs, 'Vật tư');
            
            // Generate Excel file
            XLSX.writeFile(wb, `${projectName}_Vật tư.xlsx`);
            
            showNotification('Đã xuất vật tư ra Excel', 'success');
        }

        // Show Notification
        function showNotification(message, type) {
            notificationMessage.textContent = message;
            notification.className = `notification notification-${type}`;
            notification.classList.add('show');
            
            setTimeout(() => {
                notification.classList.remove('show');
            }, 3000);
        }

        // Format Currency
        function formatCurrency(value) {
            return new Intl.NumberFormat('vi-VN').format(value);
        }

        // Format Compact Currency
        function formatCompactCurrency(value) {
            if (value >= 1000000) {
                return (value / 1000000).toFixed(1) + 'Tr';
            } else if (value >= 1000) {
                return (value / 1000).toFixed(0) + 'K';
            }
            return value;
        }
    </script>
</body>
</html>

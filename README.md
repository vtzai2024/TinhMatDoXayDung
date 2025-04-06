<!-- Replace your current title section with this -->
<div class="flex flex-col md:flex-row items-center justify-center mb-4 gap-4">
  <a href="https://vtzspaxe.com/" target="_blank" class="shrink-0">
    <img src="LOGO VUONG NEN TRANG 2 copy.jpg" alt="VTZ SPAXE Logo" class="h-16 hover:opacity-80 transition-opacity">
  </a>
  <div class="text-center md:text-left">
    <h1 class="text-2xl font-bold text-indigo-700">BẢNG TÍNH MẬT ĐỘ XÂY DỰNG TP.HCM</h1>
    <p class="text-gray-600">Theo Phụ lục 18 - Quyết định số 56/2021/QĐ-UBND</p>
  </div>
<style>
  .logo-container {
    display: flex;
    justify-content: center;
    margin-bottom: 1rem;
  }
  .logo-container img {
    height: 80px; /* Adjust size as needed */
    transition: transform 0.3s ease;
  }
  .logo-container img:hover {
    transform: scale(1.05); /* Add a slight hover effect */
  }
</style>
</div>
<TinhMatDoXayDung-VTZ.Spaxe html>
<html lang="vi">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>BẢNG TÍNH MẬT ĐỘ XÂY DỰNG TP.HCM - QĐ-56-2021-UBND</title>
    <link href="https://cdn.jsdelivr.net/npm/tailwindcss@2.2.19/dist/tailwind.min.css" rel="stylesheet">
    <link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/@fortawesome/fontawesome-free@6.2.1/css/all.min.css">
    <style>
        body {
            font-family: system-ui, -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Open Sans', 'Helvetica Neue', sans-serif;
            line-height: 1.6;
        }
        .table-container {
            overflow-x: auto;
        }
        table {
            width: 100%;
            border-collapse: collapse;
        }
        th, td {
            border: 1px solid #e2e8f0;
            padding: 0.5rem;
            text-align: center;
        }
        th {
            background-color: #f8fafc;
        }
        .result-section {
            opacity: 0;
            max-height: 0;
            overflow: hidden;
            transition: all 0.5s ease;
        }
        .result-section.active {
            opacity: 1;
            max-height: 3000px;
        }
        @media print {
            @page {
                size: auto;
                margin: 10mm;
            }
            input, select, button {
                border: 1px solid #ccc !important;
            }
            .no-print {
                display: none;
            }
            .print-break-inside-avoid {
                break-inside: avoid;
            }
        }
        .tooltip {
            position: relative;
            display: inline-block;
            cursor: help;
        }
        .tooltip .tooltiptext {
            visibility: hidden;
            width: 240px;
            background-color: #555;
            color: #fff;
            text-align: left;
            border-radius: 6px;
            padding: 8px;
            position: absolute;
            z-index: 1;
            bottom: 125%;
            left: 50%;
            transform: translateX(-50%);
            opacity: 0;
            transition: opacity 0.3s;
            font-size: 0.85rem;
            box-shadow: 0 2px 5px rgba(0,0,0,0.2);
        }
        .tooltip:hover .tooltiptext {
            visibility: visible;
            opacity: 1;
        }
    </style>
</head>
<body class="bg-gray-50 p-4 md:p-8">
    <div class="max-w-4xl mx-auto bg-white shadow-md rounded-lg p-6">
        <h1 class="text-2xl md:text-3xl font-bold text-center text-indigo-800 mb-6 border-b pb-4">
            BẢNG TÍNH MẬT ĐỘ XÂY DỰNG TP.HCM<br>
            <span class="text-lg md:text-xl font-medium text-gray-600">Theo Phụ lục 18 - Quyết định số 56/2021/QĐ-UBND</span>
        </h1>

        <div class="mb-8">
            <h2 class="text-xl font-bold text-indigo-700 mb-4">Nhập thông tin lô đất</h2>
            <form id="calculatorForm" class="grid grid-cols-1 md:grid-cols-2 gap-4">
                <div class="form-group">
                    <label for="plotArea" class="block font-medium text-gray-700 mb-1">Diện tích lô đất (m²):</label>
                    <input type="number" id="plotArea" name="plotArea" min="0" step="0.01" required
                        class="w-full px-3 py-2 border border-gray-300 rounded-md focus:outline-none focus:ring-2 focus:ring-indigo-500">
                    <small class="text-gray-500">Diện tích lô đất ảnh hưởng đến mật độ xây dựng tối đa</small>
                </div>

                <div class="form-group">
                    <label for="plotDepth" class="block font-medium text-gray-700 mb-1">Chiều sâu D (m) tính từ ranh lộ giới:</label>
                    <input type="number" id="plotDepth" name="plotDepth" min="0" step="0.01" required
                        class="w-full px-3 py-2 border border-gray-300 rounded-md focus:outline-none focus:ring-2 focus:ring-indigo-500">
                    <small class="text-gray-500">Chiều sâu lô đất ảnh hưởng đến yêu cầu khoảng lùi</small>
                </div>

                <div class="form-group">
                    <label for="streetWidth" class="block font-medium text-gray-700 mb-1">Chiều rộng lộ giới (m):</label>
                    <input type="number" id="streetWidth" name="streetWidth" min="0" step="0.01" required
                        class="w-full px-3 py-2 border border-gray-300 rounded-md focus:outline-none focus:ring-2 focus:ring-indigo-500">
                    <small class="text-gray-500">Chiều rộng lộ giới ảnh hưởng đến số tầng và chiều cao tối đa</small>
                </div>

                <div class="form-group">
                    <label for="facadeWidth" class="block font-medium text-gray-700 mb-1">Chiều rộng mặt tiền (m):</label>
                    <input type="number" id="facadeWidth" name="facadeWidth" min="0" step="0.01" required
                        class="w-full px-3 py-2 border border-gray-300 rounded-md focus:outline-none focus:ring-2 focus:ring-indigo-500">
                    <small class="text-gray-500">Mặt tiền > 8m có thể được cộng thêm tầng</small>
                </div>

                <div class="form-group md:col-span-2 grid grid-cols-1 md:grid-cols-2 gap-4 mt-2">
                    <div class="checkbox-group">
                        <label class="inline-flex items-center">
                            <input type="checkbox" id="centralDistrict" name="centralDistrict" class="form-checkbox h-5 w-5 text-indigo-600">
                            <span class="ml-2 text-gray-700">Thuộc Quận trung tâm hoặc Trung tâm cấp quận</span>
                            <span class="tooltip ml-1 text-gray-500">
                                <i class="fas fa-question-circle"></i>
                                <span class="tooltiptext">Các quận trung tâm hoặc khu vực được xác định là trung tâm cấp quận trong quy hoạch.</span>
                            </span>
                        </label>
                    </div>

                    <div class="checkbox-group">
                        <label class="inline-flex items-center">
                            <input type="checkbox" id="commercialStreet" name="commercialStreet" class="form-checkbox h-5 w-5 text-indigo-600">
                            <span class="ml-2 text-gray-700">Thuộc trục đường thương mại - dịch vụ</span>
                            <span class="tooltip ml-1 text-gray-500">
                                <i class="fas fa-question-circle"></i>
                                <span class="tooltiptext">Các trục đường được xác định là thương mại - dịch vụ trong Phụ lục 02 của Quy chế.</span>
                            </span>
                        </label>
                    </div>
                </div>

                <div class="md:col-span-2 mt-4">
                    <button type="submit" id="calculateBtn" class="bg-indigo-600 text-white px-6 py-2 rounded-md hover:bg-indigo-700 focus:outline-none focus:ring-2 focus:ring-indigo-500 focus:ring-offset-2 w-full md:w-auto">
                        Tính toán
                    </button>
                </div>
            </form>
        </div>

        <div id="resultsSection" class="result-section border-t pt-6">
            <h2 class="text-xl font-bold text-indigo-700 mb-4">Kết quả tính toán</h2>
            
            <!-- Thông tin cơ bản -->
            <div class="mb-6 p-4 bg-gray-50 rounded-lg print-break-inside-avoid">
                <h3 class="font-bold text-lg text-indigo-600 mb-2">Thông tin cơ bản</h3>
                <div class="grid grid-cols-1 md:grid-cols-2 gap-4">
                    <div>
                        <p><span class="font-medium">Diện tích lô đất:</span> <span id="result-plotArea"></span> m²</p>
                        <p><span class="font-medium">Chiều sâu lô đất:</span> <span id="result-plotDepth"></span> m</p>
                    </div>
                    <div>
                        <p><span class="font-medium">Chiều rộng lộ giới:</span> <span id="result-streetWidth"></span> m</p>
                        <p><span class="font-medium">Chiều rộng mặt tiền:</span> <span id="result-facadeWidth"></span> m</p>
                    </div>
                </div>
                <div id="specialConditionsResult" class="mt-2"></div>
            </div>

            <!-- Mật độ xây dựng -->
            <div class="mb-6 p-4 bg-blue-50 rounded-lg print-break-inside-avoid">
                <h3 class="font-bold text-lg text-blue-700 mb-2">1. Mật độ xây dựng</h3>
                <p class="font-semibold text-2xl text-blue-700 mb-2"><span id="result-density"></span>%</p>
                <div id="density-explanation" class="text-sm text-gray-600"></div>
            </div>

            <!-- Khoảng lùi -->
            <div class="mb-6 p-4 bg-green-50 rounded-lg print-break-inside-avoid">
                <h3 class="font-bold text-lg text-green-700 mb-2">2. Khoảng lùi xây dựng</h3>
                <div id="setback-results" class="mb-2"></div>
                <div id="setback-explanation" class="text-sm text-gray-600"></div>
            </div>

            <!-- Số tầng -->
            <div class="mb-6 p-4 bg-purple-50 rounded-lg print-break-inside-avoid">
                <h3 class="font-bold text-lg text-purple-700 mb-2">3. Số tầng tối đa</h3>
                <p class="font-semibold text-2xl text-purple-700 mb-2"><span id="result-floors"></span> tầng</p>
                <div id="floor-details"></div>
                <div id="floor-explanation" class="text-sm text-gray-600 mt-2"></div>
            </div>

            <!-- Chiều cao -->
            <div class="mb-6 p-4 bg-red-50 rounded-lg print-break-inside-avoid">
                <h3 class="font-bold text-lg text-red-700 mb-2">4. Chiều cao tối đa</h3>
                <div id="height-results" class="mb-2"></div>
                <div id="height-explanation" class="text-sm text-gray-600"></div>
            </div>

            <!-- Lưu ý đặc biệt -->
            <div id="special-notes" class="mb-6 p-4 bg-yellow-50 rounded-lg print-break-inside-avoid">
                <h3 class="font-bold text-lg text-yellow-700 mb-2">Lưu ý đặc biệt</h3>
                <div id="special-notes-content"></div>
            </div>
        </div>
        
        <div class="mt-8 pt-6 border-t text-center text-gray-500 text-sm">
            <p>Máy tính này chỉ để tham khảo dựa trên Quyết định số 56/2021/QĐ-UBND.</p>
            <p>Vui lòng liên hệ cơ quan có thẩm quyền để được hướng dẫn cụ thể khi thực hiện xây dựng.</p>
        </div>
    </div>

    <script>
        document.addEventListener('DOMContentLoaded', function() {
            const form = document.getElementById('calculatorForm');
            const resultsSection = document.getElementById('resultsSection');
            
            form.addEventListener('submit', function(e) {
                e.preventDefault();
                calculateResults();
                // Hiển thị kết quả
                resultsSection.classList.add('active');
                // Cuộn đến phần kết quả
                resultsSection.scrollIntoView({ behavior: 'smooth' });
            });

            // Thực hiện tính toán và hiển thị kết quả
            function calculateResults() {
                // Lấy giá trị đầu vào
                const plotArea = parseFloat(document.getElementById('plotArea').value);
                const plotDepth = parseFloat(document.getElementById('plotDepth').value);
                const streetWidth = parseFloat(document.getElementById('streetWidth').value);
                const facadeWidth = parseFloat(document.getElementById('facadeWidth').value);
                const centralDistrict = document.getElementById('centralDistrict').checked;
                const commercialStreet = document.getElementById('commercialStreet').checked;

                // Hiển thị thông tin cơ bản
                document.getElementById('result-plotArea').textContent = plotArea.toFixed(2);
                document.getElementById('result-plotDepth').textContent = plotDepth.toFixed(2);
                document.getElementById('result-streetWidth').textContent = streetWidth.toFixed(2);
                document.getElementById('result-facadeWidth').textContent = facadeWidth.toFixed(2);

                // Hiển thị điều kiện đặc biệt
                let specialConditionsText = '';
                if (centralDistrict || commercialStreet || facadeWidth > 8.0) {
                    specialConditionsText += '<p class="font-medium mt-2">Điều kiện đặc biệt:</p><ul class="list-disc list-inside">';
                    if (centralDistrict) {
                        specialConditionsText += '<li>Thuộc Quận trung tâm hoặc Trung tâm cấp quận</li>';
                    }
                    if (commercialStreet) {
                        specialConditionsText += '<li>Thuộc trục đường thương mại - dịch vụ</li>';
                    }
                    if (facadeWidth > 8.0) {
                        specialConditionsText += '<li>Chiều rộng mặt tiền > 8,0m</li>';
                    }
                    specialConditionsText += '</ul>';
                } else {
                    specialConditionsText = '<p class="font-medium mt-2">Không có điều kiện đặc biệt áp dụng</p>';
                }
                document.getElementById('specialConditionsResult').innerHTML = specialConditionsText;

                // 1. Tính mật độ xây dựng (Bảng 1)
                const density = calculateBuildingDensity(plotArea);
                document.getElementById('result-density').textContent = density.toFixed(1);
                
                // Giải thích mật độ xây dựng
                let densityExplanation = '';
                if (plotArea < 50) {
                    densityExplanation = 'Với diện tích lô đất dưới 50m², mật độ xây dựng tối đa là 100%.';
                } else if (plotArea > 500) {
                    densityExplanation = 'Với diện tích lô đất trên 500m², mật độ xây dựng tối đa là 50%.';
                } else {
                    densityExplanation = `Với diện tích lô đất ${plotArea}m², mật độ xây dựng tối đa được tính theo công thức nội suy từ Bảng 1 Phụ lục 18.`;
                }
                document.getElementById('density-explanation').innerHTML = densityExplanation;

                // 2. Tính khoảng lùi
                const setbacks = calculateSetbacks(plotArea, plotDepth, commercialStreet);
                let setbackResults = '';
                let setbackExplanation = '';

                if (setbacks.rear > 0) {
                    setbackResults += `<p class="font-semibold text-xl text-green-700">Khoảng lùi phía sau: ${setbacks.rear} m</p>`;
                } else {
                    setbackResults += `<p class="font-semibold text-xl text-green-700">Không yêu cầu khoảng lùi phía sau</p>`;
                }

                if (setbacks.front > 0) {
                    setbackResults += `<p class="font-semibold text-xl text-green-700 mt-2">Khoảng lùi mặt tiền tầng 1: ${setbacks.front} m</p>`;
                    if (commercialStreet) {
                        setbackExplanation += `<p>Do lô đất nằm trên trục đường thương mại - dịch vụ, phải thiết kế có khoảng lùi tại mặt tiền Tầng 1 (Tầng trệt) ${setbacks.front}m so với ranh lộ giới.</p>`;
                    }
                }

                if (plotArea > 50) {
                    if (plotDepth >= 16) {
                        setbackExplanation += `<p>Với chiều sâu lô đất ${plotDepth}m ≥ 16m, công trình phải bố trí khoảng lùi so với ranh đất sau tối thiểu 2m.</p>`;
                    } else if (plotDepth >= 9) {
                        setbackExplanation += `<p>Với chiều sâu lô đất ${plotDepth}m (9m ≤ D < 16m), công trình phải bố trí khoảng lùi so với ranh đất sau tối thiểu 1m.</p>`;
                    } else {
                        setbackExplanation += `<p>Với chiều sâu lô đất ${plotDepth}m < 9m, khuyến khích tạo khoảng trống phía sau nhà.</p>`;
                    }
                } else {
                    setbackExplanation += `<p>Với diện tích lô đất dưới 50m², không có yêu cầu cụ thể về khoảng lùi phía sau.</p>`;
                }

                document.getElementById('setback-results').innerHTML = setbackResults;
                document.getElementById('setback-explanation').innerHTML = setbackExplanation;

                // 3. Tính số tầng tối đa (Bảng 2)
                const { baseFloors, additionalFloors, maxFloors, restrictions } = calculateFloors(streetWidth, facadeWidth, centralDistrict, commercialStreet);
                document.getElementById('result-floors').textContent = maxFloors;

                // Chi tiết về số tầng
                let floorDetails = `<p>Số tầng cơ bản: <span class="font-medium">${baseFloors} tầng</span></p>`;
                
                if (additionalFloors > 0) {
                    floorDetails += `<p>Số tầng cộng thêm: <span class="font-medium">+${additionalFloors} tầng</span></p>`;
                    floorDetails += `<p class="text-sm italic">Các tầng cộng thêm phải lùi vào so với chỉ giới xây dựng 3,5m</p>`;
                }
                
                document.getElementById('floor-details').innerHTML = floorDetails;

                // Giải thích số tầng
                let floorExplanation = '';
                if (streetWidth >= 25) {
                    floorExplanation = `Với chiều rộng lộ giới ${streetWidth}m ≥ 25m, số tầng cơ bản là 6 tầng, không được phép cộng thêm tầng.`;
                } else {
                    floorExplanation = `Với chiều rộng lộ giới ${streetWidth}m, số tầng cơ bản là ${baseFloors} tầng.`;
                    
                    if (facadeWidth < 4.0) {
                        floorExplanation += ` Do chiều rộng mặt tiền < 4,0m, không được phép cộng thêm tầng.`;
                    } else {
                        if (additionalFloors > 0) {
                            let reasons = [];
                            if (centralDistrict && streetWidth < 25) reasons.push("thuộc Quận trung tâm/Trung tâm cấp quận");
                            if (commercialStreet && streetWidth >= 16 && streetWidth < 25) reasons.push("thuộc trục đường thương mại - dịch vụ");
                            if (facadeWidth > 8.0 && streetWidth < 25) reasons.push("chiều rộng mặt tiền > 8,0m");
                            
                            if (reasons.length > 0) {
                                floorExplanation += ` Được cộng thêm ${additionalFloors} tầng do ${reasons.join(", ")}.`;
                            }
                        } else {
                            floorExplanation += ` Không có điều kiện để cộng thêm tầng.`;
                        }
                    }
                }
                
                document.getElementById('floor-explanation').innerHTML = floorExplanation;

                // 4. Tính chiều cao tối đa (Bảng 3)
                const heights = calculateBuildingHeight(streetWidth, maxFloors, additionalFloors > 0);
                
                // Hiển thị chiều cao
                let heightResults = '';
                heightResults += `<p class="font-semibold text-xl text-red-700">Chiều cao tại chỉ giới xây dựng: ${heights.standardHeight} m</p>`;
                heightResults += `<p class="font-semibold text-xl text-red-700 mt-2">Chiều cao tối đa tại đỉnh mái: ${heights.maxHeight} m</p>`;
                
                document.getElementById('height-results').innerHTML = heightResults;

                // Giải thích chiều cao
                let heightExplanation = `Với chiều rộng lộ giới ${streetWidth}m và số tầng tối đa ${maxFloors} tầng, chiều cao tối đa tại chỉ giới xây dựng là ${heights.standardHeight}m và chiều cao tối đa tại đỉnh mái là ${heights.maxHeight}m.`;
                if (additionalFloors > 0) {
                    heightExplanation += ` Chiều cao này đã tính đến việc có ${additionalFloors} tầng cộng thêm.`;
                }
                
                document.getElementById('height-explanation').innerHTML = heightExplanation;

                // 5. Lưu ý đặc biệt
                let specialNotes = '';
                
                // Kiểm tra các trường hợp đặc biệt
                if (plotArea < 36) {
                    specialNotes += `<p class="mb-2 text-yellow-800"><i class="fas fa-exclamation-triangle mr-2"></i>Lô đất có diện tích ${plotArea}m² < 36m², có quy định đặc biệt về chiều cao.</p>`;
                    
                    if (plotArea < 15) {
                        specialNotes += `<p class="ml-4 mb-2">- Lô đất có diện tích nhỏ hơn 15m²: chỉ được cải tạo, sửa chữa theo hiện trạng hoặc xây dựng mới với chiều cao tối đa tại đỉnh mái không quá 7,0m.</p>`;
                    } else {
                        // Lô đất từ 15m² đến dưới 36m²
                        if (streetWidth >= 6) {
                            specialNotes += `<p class="ml-4 mb-2">- Lô đất tiếp giáp đường có lộ giới từ 6m trở lên: chiều cao tối đa tại chỉ giới xây dựng không quá 11,6m và chiều cao tối đa tại đỉnh mái không quá 13,6m.</p>`;
                        } else {
                            specialNotes += `<p class="ml-4 mb-2">- Lô đất tiếp giáp đường có lộ giới nhỏ hơn 6m: chiều cao tối đa tại đỉnh mái không quá 11,6m.</p>`;
                        }
                    }
                }
                
                if (facadeWidth < 3.0) {
                    specialNotes += `<p class="mb-2 text-yellow-800"><i class="fas fa-exclamation-triangle mr-2"></i>Lô đất có chiều rộng mặt tiền ${facadeWidth}m < 3,0m: chỉ được cải tạo, sửa chữa theo quy mô hiện trạng hoặc xây dựng mới với chiều cao tối đa tại chỉ giới xây dựng 7,0m. Chiều cao tại đỉnh mái không quá 9,0m.</p>`;
                }
                
                if (plotArea > 500) {
                    specialNotes += `<p class="mb-2 text-yellow-800"><i class="fas fa-exclamation-triangle mr-2"></i>Lô đất có diện tích ${plotArea}m² > 500m²: sẽ do cơ quan quản lý kiến trúc quy hoạch có thẩm quyền xem xét và cung cấp thông tin quy hoạch đô thị cụ thể.</p>`;
                }

                if (specialNotes === '') {
                    document.getElementById('special-notes').style.display = 'none';
                } else {
                    document.getElementById('special-notes').style.display = 'block';
                    document.getElementById('special-notes-content').innerHTML = specialNotes;
                }
            }

            // Hàm tính mật độ xây dựng (Bảng 1)
            function calculateBuildingDensity(plotArea) {
                // Các điểm chuẩn từ Bảng 1
                const densityTable = [
                    {area: 50, density: 100},
                    {area: 100, density: 90},
                    {area: 200, density: 70},
                    {area: 300, density: 60},
                    {area: 500, density: 50}
                ];
                
                // Trường hợp đặc biệt
                if (plotArea < densityTable[0].area) {
                    return densityTable[0].density;
                }
                if (plotArea >= densityTable[densityTable.length - 1].area) {
                    return densityTable[densityTable.length - 1].density;
                }
                
                // Tìm cận trên và cận dưới
                let lowerBound = null;
                let upperBound = null;
                
                for (let i = 0; i < densityTable.length - 1; i++) {
                    if (plotArea >= densityTable[i].area && plotArea < densityTable[i + 1].area) {
                        lowerBound = densityTable[i];
                        upperBound = densityTable[i + 1];
                        break;
                    }
                }
                
                // Tính mật độ bằng công thức nội suy
                // Nt = Nb - (Nb - Na) × (Ct - Cb) / (Ca - Cb)
                const Nt = lowerBound.density - (lowerBound.density - upperBound.density) * 
                          (plotArea - lowerBound.area) / (upperBound.area - lowerBound.area);
                          
                return Nt;
            }

            // Hàm tính khoảng lùi
            function calculateSetbacks(plotArea, plotDepth, commercialStreet) {
                let rear = 0;
                let front = 0;
                
                // Khoảng lùi phía sau cho lô đất > 50m²
                if (plotArea > 50) {
                    if (plotDepth >= 16) {
                        rear = 2;
                    } else if (plotDepth >= 9) {
                        rear = 1;
                    }
                }
                
                // Khoảng lùi mặt tiền cho trục đường thương mại - dịch vụ
                if (commercialStreet) {
                    front = (plotDepth < 6) ? 1.5 : 3;
                }
                
                return { rear, front };
            }

            // Hàm tính số tầng tối đa (Bảng 2)
            function calculateFloors(streetWidth, facadeWidth, centralDistrict, commercialStreet) {
                let baseFloors = 0;
                let additionalFloors = 0;
                let restrictions = [];
                
                // Xác định số tầng cơ bản
                if (streetWidth >= 25) {
                    baseFloors = 6;
                } else if (streetWidth >= 16) {
                    baseFloors = 5;
                } else if (streetWidth >= 6) {
                    baseFloors = 4;
                } else if (streetWidth >= 3.5) {
                    baseFloors = 3;
                } else {
                    baseFloors = 3;
                }
                
                // Kiểm tra điều kiện không được cộng thêm tầng
                if (facadeWidth < 4.0) {
                    restrictions.push("Chiều rộng mặt tiền < 4,0m không được cộng thêm tầng");
                } else {
                    // Tính số tầng cộng thêm
                    if (streetWidth >= 25) {
                        // Không cộng thêm tầng khi lộ giới ≥ 25m
                        additionalFloors = 0;
                    } else if (streetWidth >= 16) {
                        // 16 ≤ L < 25
                        if (centralDistrict) additionalFloors++;
                        if (commercialStreet) additionalFloors++;
                        if (facadeWidth > 8.0) additionalFloors++;
                        additionalFloors = Math.min(additionalFloors, 1); // Tối đa 1 tầng
                    } else if (streetWidth >= 6) {
                        // 6 ≤ L < 16
                        if (centralDistrict) additionalFloors++;
                        if (facadeWidth > 8.0) additionalFloors++;
                        additionalFloors = Math.min(additionalFloors, 1); // Tối đa 1 tầng
                    } else if (streetWidth >= 3.5) {
                        // 3,5 ≤ L < 6
                        if (centralDistrict) additionalFloors++;
                        if (facadeWidth > 8.0) additionalFloors++;
                        additionalFloors = Math.min(additionalFloors, 1); // Tối đa 1 tầng
                    } else {
                        // L < 3,5
                        additionalFloors = 0;
                    }
                }
                
                const maxFloors = baseFloors + additionalFloors;
                
                return { baseFloors, additionalFloors, maxFloors, restrictions };
            }

            // Hàm tính chiều cao tối đa (Bảng 3)
            function calculateBuildingHeight(streetWidth, floors, hasAdditionalFloors) {
                let standardHeight = 0;
                let maxHeight = 0;
                
                // Xác định chiều cao theo Bảng 3
                if (streetWidth >= 25) {
                    standardHeight = 25.0;
                    maxHeight = 27.0;
                } else if (streetWidth >= 16) {
                    standardHeight = 21.6;
                    maxHeight = hasAdditionalFloors ? 27.0 : 23.6;
                } else if (streetWidth >= 6) {
                    standardHeight = 17.0;
                    maxHeight = hasAdditionalFloors ? 22.4 : 19.0;
                } else if (streetWidth >= 3.5) {
                    standardHeight = 11.6;
                    maxHeight = hasAdditionalFloors ? 15.6 : 13.6;
                } else {
                    standardHeight = 9.0; // Ước tính
                    maxHeight = 11.6;
                }
                
                return { standardHeight, maxHeight };
            }
        });
    </script>
</body>
</html>

<!DOCTYPE html>
<html lang="th">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>สรุปความขัดแย้งไทย-กัมพูชา: ประวัติศาสตร์และการวิเคราะห์</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
    <link href="https://fonts.googleapis.com/css2?family=Sarabun:wght@300;400;600;700&display=swap" rel="stylesheet">
    <!-- Chosen Palette: Warm Historical - Cream/Paper background (#F9F5F0), Deep Brown Text (#4A3B32), Terracotta Accent (#C05640), Muted Gold (#D4A017) for highlights. Designed to evoke history and seriousness without being dull. -->
    
    <!-- Application Structure Plan: 
         The app uses a 'Timeline Dashboard' structure. Instead of a long scrolling page, it features a prominent top navigation timeline that segments the history into 4 distinct eras (Ancient, Cold War, Preah Vihear, Current). 
         Why? The conflict spans centuries with distinct characteristics in each era. A tabbed/timeline approach allows users to focus on the specific dynamics of each period without losing context.
         
         Layout:
         1. Hero Section: Title and intro.
         2. Interactive Timeline: Buttons representing the 4 eras.
         3. Dynamic Content Area:
            - Left Column: Narrative details, key events list, and qualitative insights.
            - Right Column: A dedicated Visualization Panel showing a dynamic chart relevant to that specific era (e.g., Power shifts, Conflict intensity, Incident types).
         4. Footer: Summary/Synthesis.
         
         Key Interactions: Clicking a timeline node updates the content and destroys/renders a new chart.
    -->

    <!-- Visualization & Content Choices:
         1. Ancient Era: 
            - Goal: Show the shift in power. 
            - Viz: Bar Chart comparing "Strategic Influence" of Ayutthaya vs. Khmer Empire. 
            - Interaction: Tooltips showing specific battles (1431, 1593).
            - Justification: Visualizes the 'rise and fall' dynamic described in the text.
         
         2. Cold War Era: 
            - Goal: Illustrate the frequency/intensity of border incidents over time.
            - Viz: Line Chart (1975-1989) showing estimated tension levels based on text (Khmer Rouge raids -> Full Vietnam War).
            - Interaction: Points on line show event details (Trat raid, Chong Bok battle).
            - Justification: Shows the escalation from raids to full conventional warfare.
            
         3. Preah Vihear Crisis: 
            - Goal: Breakdown the 2011 crisis components.
            - Viz: Doughnut Chart or Horizontal Bar showing "Impact Distribution" (Casualties, Displacement, Diplomatic Fallout). Let's use a Bar Chart for "Conflict Intensity by Event" (Registration vs 2011 Clashes).
            - Interaction: Bars reveal specific outcomes (ICJ ruling details).
            - Justification: Highlights the peak violence in 2011 compared to the initial 2008 trigger.
            
         4. Current Era: 
            - Goal: Categorize current friction points.
            - Viz: Radar Chart showing "Conflict Drivers" (Demarcation, Construction, Patrols, Politics).
            - Interaction: Hover to see details of specific hotspots (Ta Muen Thom).
            - Justification: Shows the multi-faceted nature of modern, lower-intensity conflict.
            
         CONFIRMATION: NO SVG graphics used. NO Mermaid JS used. All visuals via HTML/CSS/Canvas.
    -->

    <style>
        body {
            font-family: 'Sarabun', sans-serif;
            background-color: #F9F5F0;
            color: #4A3B32;
        }
        .chart-container {
            position: relative;
            width: 100%;
            max-width: 600px;
            margin-left: auto;
            margin-right: auto;
            height: 300px;
            max-height: 400px;
        }
        @media (min-width: 768px) {
            .chart-container {
                height: 350px;
            }
        }
        .active-tab {
            background-color: #C05640;
            color: white;
            border-color: #C05640;
        }
        .inactive-tab {
            background-color: #E5E0D8;
            color: #7D6E63;
            border-color: #D1C7BD;
        }
        .inactive-tab:hover {
            background-color: #D1C7BD;
        }
        .fade-in {
            animation: fadeIn 0.5s ease-in-out;
        }
        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(10px); }
            to { opacity: 1; transform: translateY(0); }
        }
    </style>
</head>
<body class="flex flex-col min-h-screen">

    <!-- Header Section -->
    <header class="bg-[#4A3B32] text-[#F9F5F0] py-6 shadow-md">
        <div class="container mx-auto px-4 text-center">
            <h1 class="text-3xl md:text-4xl font-bold mb-2">มหากาพย์ความขัดแย้ง: ไทย - กัมพูชา</h1>
            <p class="text-lg opacity-80 max-w-2xl mx-auto">
                วิเคราะห์วิวัฒนาการความขัดแย้งจากสงครามแย่งชิงอำนาจยุคจารีต สู่ข้อพิพาทเขตแดนสมัยใหม่
            </p>
        </div>
    </header>

    <!-- Main Content Container -->
    <main class="flex-grow container mx-auto px-4 py-8">

        <!-- Introduction Block -->
        <div class="bg-white rounded-lg shadow-sm p-6 mb-8 border-l-4 border-[#C05640]">
            <h2 class="text-xl font-bold mb-3 text-[#C05640]">ภาพรวมความขัดแย้ง</h2>
            <p class="leading-relaxed">
                ความสัมพันธ์ระหว่างไทย (สยาม) และกัมพูชาเต็มไปด้วยประวัติศาสตร์อันยาวนานและซับซ้อน 
                แอพพลิเคชั่นนี้สรุปเหตุการณ์สำคัญโดยแบ่งออกเป็น 4 ยุคหลัก 
                เพื่อให้ท่านสามารถสำรวจพลวัตของการเปลี่ยนแปลงอำนาจ 
                จากสงครามแย่งชิงความเป็นใหญ่ในภูมิภาคสู่ข้อพิพาทเรื่องเส้นเขตแดนและมรดกโลกในปัจจุบัน 
                ท่านสามารถเลือกช่วงเวลาจากไทม์ไลน์ด้านล่างเพื่อเจาะลึกข้อมูลและการวิเคราะห์เชิงลึก
            </p>
        </div>

        <!-- Interactive Timeline Navigation -->
        <div class="mb-8 overflow-x-auto pb-2">
            <div class="flex md:justify-center min-w-max md:min-w-0 space-x-4">
                <button onclick="updateEra(0)" id="tab-0" class="active-tab px-6 py-3 rounded-full font-bold shadow transition-all duration-300 flex items-center gap-2">
                    <span>๑. ยุคโบราณ & อยุธยา</span>
                </button>
                <button onclick="updateEra(1)" id="tab-1" class="inactive-tab px-6 py-3 rounded-full font-bold shadow transition-all duration-300 flex items-center gap-2">
                    <span>๒. ยุคเขมรแดง & เวียดนาม</span>
                </button>
                <button onclick="updateEra(2)" id="tab-2" class="inactive-tab px-6 py-3 rounded-full font-bold shadow transition-all duration-300 flex items-center gap-2">
                    <span>๓. วิกฤตพระวิหาร (2551-2554)</span>
                </button>
                <button onclick="updateEra(3)" id="tab-3" class="inactive-tab px-6 py-3 rounded-full font-bold shadow transition-all duration-300 flex items-center gap-2">
                    <span>๔. สถานการณ์ปัจจุบัน</span>
                </button>
            </div>
        </div>

        <!-- Dynamic Content Section -->
        <div id="content-area" class="grid grid-cols-1 lg:grid-cols-2 gap-8 fade-in">
            
            <!-- Left Column: Narrative & Details -->
            <div class="bg-white rounded-xl shadow-lg p-6 md:p-8">
                <div class="flex items-center gap-3 mb-6">
                    <span id="era-icon" class="text-3xl">⚔️</span>
                    <!-- เปลี่ยน text-2xl เป็น text-3xl เพื่อให้หัวข้อใหญ่ขึ้น -->
                    <h2 id="era-title" class="text-3xl font-bold text-[#4A3B32]"></h2>
                </div>
                
                <div class="prose prose-stone max-w-none">
                    <!-- เปลี่ยน text-lg เป็น text-base เพื่อให้อ่านง่ายขึ้นในบล็อกข้อความ -->
                    <p id="era-description" class="mb-6 text-base leading-relaxed text-gray-700"></p>
                    
                    <!-- ปรับ mb-3 เป็น mb-4 และ pb-2 เป็น pb-3 เพื่อเพิ่มช่องไฟให้หัวข้อเหตุการณ์สำคัญ -->
                    <h3 class="font-bold text-lg text-[#C05640] mb-4 border-b border-gray-200 pb-3">เหตุการณ์สำคัญ</h3>
                    <ul id="era-events" class="space-y-4">
                        <!-- Events populated by JS -->
                    </ul>
                </div>
            </div>

            <!-- Right Column: Visualization & Analysis -->
            <div class="flex flex-col gap-6">
                <!-- Chart Card -->
                <div class="bg-white rounded-xl shadow-lg p-6 flex flex-col items-center justify-center">
                    <h3 id="chart-title" class="text-lg font-bold text-[#4A3B32] mb-4 text-center"></h3>
                    
                    <!-- Chart Container (Strictly Constrained) -->
                    <div class="chart-container">
                        <canvas id="mainChart"></canvas>
                    </div>
                    
                    <p id="chart-caption" class="text-sm text-gray-500 mt-4 text-center italic"></p>
                </div>

                <!-- Insight Card - เพิ่ม border-l-4 เพื่อเน้นด้วยสีหลัก -->
                <div class="bg-[#F2EBE3] rounded-xl p-6 border border-[#D1C7BD] border-l-4 border-l-[#C05640]">
                    <h3 class="font-bold text-[#4A3B32] mb-2 flex items-center gap-2">
                        <span>💡</span> บทวิเคราะห์
                    </h3>
                    <p id="era-insight" class="text-sm md:text-base text-gray-700"></p>
                </div>
            </div>

        </div>

    </main>

    <!-- Footer -->
    <footer class="bg-[#4A3B32] text-[#D1C7BD] py-8 mt-8">
        <div class="container mx-auto px-4 text-center">
            <p class="text-sm">
                ข้อมูลอ้างอิงจากเอกสารสรุปเหตุการณ์ความขัดแย้งระหว่างไทย-กัมพูชา
            </p>
            <div class="mt-4 flex justify-center gap-4 text-xs">
                <span>© 2025 Thai-Cambodia Relations Summary</span>
            </div>
        </div>
    </footer>

    <!-- JavaScript Logic -->
    <script>
        // --- Data Store ---
        const eraData = [
            {
                title: "ยุคโบราณและอยุธยา (ศตวรรษที่ 15–18)",
                icon: "🏰",
                description: "ยุคแห่งการสู้รบเพื่อช่วงชิงความเป็นใหญ่ในภูมิภาคอุษาคเนย์ เป็นช่วงเวลาที่อาณาจักรอยุธยาขยายอำนาจ ในขณะที่จักรวรรดิขอม (เขมร) เริ่มเสื่อมถอยลง การทำสงครามในยุคนี้เน้นการควบคุมกำลังคนและการขยายขอบเขตอิทธิพลเหนือเมืองประเทศราช",
                events: [
                    { year: "พ.ศ. 1974 (ค.ศ. 1431)", text: "<strong>การตีกรุงยโสธรปุระ (เมืองพระนคร):</strong> กองทัพอยุธยาเข้าตีและทำลายเมืองหลวงของขอม ทำให้อาณาจักรขอมต้องย้ายเมืองหลวงลงใต้ เป็นจุดเปลี่ยนทางประวัติศาสตร์ที่สำคัญที่สุด" },
                    { year: "พ.ศ. 2134–2137", text: "<strong>สงครามสยาม-กัมพูชา:</strong> สมเด็จพระนเรศวรมหาราชยกทัพตีเมืองละแวก (Longvek) ได้สำเร็จ ทำให้กัมพูชาตกอยู่ภายใต้อิทธิพลของสยามอย่างเบ็ดเสร็จ" }
                ],
                insight: "ความขัดแย้งในยุคนี้เป็นรูปแบบ 'ราชาธิราช' ที่เน้นบารมีเหนือดินแดน ผลลัพธ์คือการถ่ายเทวัฒนธรรมและประชากร ระหว่างสยามและเขมรอย่างมหาศาล",
                chartTitle: "ดุลอำนาจในภูมิภาค (ประมาณการเชิงเปรียบเทียบ)",
                chartCaption: "กราฟแสดงการลดลงของอิทธิพลเขมรและการเพิ่มขึ้นของอำนาจอยุธยาหลังสงครามสำคัญ",
                chartConfig: {
                    type: 'bar',
                    labels: ['ก่อน พ.ศ. 1974', 'หลัง พ.ศ. 1974 (เสียกรุง)', 'พ.ศ. 2137 (เสียเมืองละแวก)'],
                    data: [
                        { label: 'อิทธิพลอาณาจักรขอม', data: [90, 50, 20], backgroundColor: '#C05640' },
                        { label: 'อิทธิพลอาณาจักรอยุธยา', data: [40, 80, 95], backgroundColor: '#D4A017' }
                    ]
                }
            },
            {
                title: "ยุคเขมรแดงและสงครามตัวแทน (พ.ศ. 2518–2532)",
                icon: "🎖️",
                description: "ช่วงเวลาที่ความขัดแย้งเปลี่ยนรูปแบบจากสงครามศักดินามาเป็นสงครามอุดมการณ์ (คอมมิวนิสต์) และความมั่นคงชายแดน ไทยต้องเผชิญภัยคุกคามจากการรุกรานของเขมรแดงและการขยายอิทธิพลของเวียดนาม",
                events: [
                    { year: "พ.ศ. 2518–2522", text: "<strong>การปะทะชายแดนเขมรแดง:</strong> กองกำลังเขมรแดงรุกรานพื้นที่ชายแดนไทย (ตราด, สระแก้ว) ปล้นสะดมภ์และอ้างสิทธิ์เหนือพื้นที่ทับซ้อน" },
                    { year: "พ.ศ. 2522–2532", text: "<strong>สงครามชายแดนไทย-เวียดนาม:</strong> การสู้รบครั้งใหญ่ เช่น สมรภูมิช่องบก (อุบลฯ) เพื่อต้านทานกองทัพเวียดนามที่บุกกัมพูชาและประชิดชายแดนไทย" }
                ],
                insight: "เป็นยุคที่ชายแดนไทย-กัมพูชามีความตึงเครียดสูงสุด มีการใช้อาวุธหนักและกำลังทางอากาศ เป็นสงครามเต็มรูปแบบเพื่อปกป้องอธิปไตย",
                chartTitle: "ระดับความรุนแรงของเหตุการณ์ชายแดน",
                chartCaption: "กราฟเส้นแสดงแนวโน้มความรุนแรงที่พุ่งสูงขึ้นในช่วงสงครามสั่งสอนและสมรภูมิช่องบก",
                chartConfig: {
                    type: 'line',
                    labels: ['2518 (เขมรแดงครองเมือง)', '2520 (การโจมตีหมู่บ้านไทย)', '2522 (เวียดนามบุก)', '2528 (สมรภูมิช่องบก)', '2532 (ถอนทหาร)'],
                    data: [
                        { label: 'ดัชนีความตึงเครียด', data: [60, 80, 90, 100, 40], borderColor: '#C05640', backgroundColor: 'rgba(192, 86, 64, 0.2)', fill: true, tension: 0.4 }
                    ]
                }
            },
            {
                title: "วิกฤตปราสาทพระวิหาร (พ.ศ. 2551–2554)",
                icon: "🏛️",
                description: "ความขัดแย้งในยุคโลกาภิวัตน์ที่ถูกจุดชนวนด้วยการขึ้นทะเบียนมรดกโลกและกระแสชาตินิยม นำไปสู่การเผชิญหน้าทางทหารที่รุนแรงที่สุดในรอบทศวรรษ",
                events: [
                    { year: "พ.ศ. 2551", text: "<strong>จุดเริ่มต้นวิกฤต:</strong> กัมพูชาขึ้นทะเบียนปราสาทพระวิหารเป็นมรดกโลกฝ่ายเดียว เกิดการประท้วงและการเสริมกำลังทหาร" },
                    { year: "ก.พ. & เม.ย. 2554", text: "<strong>การปะทะด้วยอาวุธหนัก:</strong> การยิงปืนใหญ่ตอบโต้กันบริเวณเขาพระวิหาร, ปราสาทตาเมือนธม และปราสาทตาควาย มีผู้เสียชีวิตและบาดเจ็บทั้งสองฝ่าย" },
                    { year: "พ.ศ. 2554", text: "<strong>ศาลโลก (ICJ):</strong> มีคำสั่งมาตรการชั่วคราวให้กำหนดเขตปลอดทหาร (PDZ) รอบตัวปราสาท เพื่อลดการเผชิญหน้า" }
                ],
                insight: "ความขัดแย้งนี้แสดงให้เห็นถึงการใช้ประเด็นประวัติศาสตร์เป็นเครื่องมือทางการเมือง และบทบาทขององค์กรระหว่างประเทศ (UNESCO, ICJ) ในการไกล่เกลี่ย",
                chartTitle: "ความเสียหายและผลกระทบ (พ.ศ. 2554)",
                chartCaption: "เปรียบเทียบพื้นที่ที่ได้รับผลกระทบจากการปะทะในจุดต่างๆ",
                chartConfig: {
                    type: 'bar',
                    labels: ['เขาพระวิหาร', 'ตาเมือนธม/ตาควาย', 'ชุมชนชายแดน'],
                    data: [
                        { label: 'ความหนักหน่วงของการปะทะ (เต็ม 10)', data: [10, 8, 6], backgroundColor: ['#C05640', '#D4A017', '#4A3B32'] }
                    ]
                }
            },
            {
                title: "สถานการณ์ปัจจุบันและพื้นที่พิพาท",
                icon: "🚩",
                description: "แม้สถานการณ์โดยรวมจะสงบลง แต่ปัญหายังไม่จบสิ้น การปักปันเขตแดนยังไม่สมบูรณ์ และยังมีการกระทบกระทั่งกันประปรายในพื้นที่อ้างสิทธิ์ทับซ้อน",
                events: [
                    { year: "ปัจจุบัน", text: "<strong>ช่องบก & ตาเมือนธม:</strong> ยังคงเป็นจุดเฝ้าระวังที่มีความละเอียดอ่อน มีรายงานการเผชิญหน้าจากการลาดตระเวน" },
                    { year: "ประเด็นขัดแย้ง", text: "<strong>สาเหตุหลัก:</strong> การก่อสร้างในพื้นที่ทับซ้อน, การขุดคูน้ำ, และการตีความแผนที่ที่แตกต่างกัน" }
                ],
                insight: "ความสัมพันธ์ปัจจุบันอยู่ในลักษณะ 'การบริหารจัดการความขัดแย้ง' (Conflict Management) ควบคู่ไปกับความร่วมมือทางเศรษฐกิจ",
                chartTitle: "ปัจจัยความขัดแย้งในปัจจุบัน",
                chartCaption: "สัดส่วนสาเหตุที่ทำให้เกิดความตึงเครียดตามแนวชายแดน",
                chartConfig: {
                    type: 'radar',
                    labels: ['การปักปันเขตแดน', 'การก่อสร้างรุกล้ำ', 'กระแสชาตินิยม', 'ทรัพยากรธรรมชาติ', 'การเมืองภายใน'],
                    data: [
                        { label: 'ระดับอิทธิพลต่อความขัดแย้ง', data: [90, 70, 60, 40, 50], borderColor: '#4A3B32', backgroundColor: 'rgba(74, 59, 50, 0.4)' }
                    ]
                }
            }
        ];

        let currentChart = null;

        // --- Core Functions ---

        function initApp() {
            updateEra(0); // Load first era by default
        }

        function updateEra(index) {
            const data = eraData[index];

            // 1. Update Tabs UI
            document.querySelectorAll('button[id^="tab-"]').forEach((btn, idx) => {
                if (idx === index) {
                    btn.classList.remove('inactive-tab');
                    btn.classList.add('active-tab');
                } else {
                    btn.classList.remove('active-tab');
                    btn.classList.add('inactive-tab');
                }
            });

            // 2. Update Text Content with Animation trigger
            const contentArea = document.getElementById('content-area');
            contentArea.classList.remove('fade-in');
            void contentArea.offsetWidth; // trigger reflow
            contentArea.classList.add('fade-in');

            document.getElementById('era-icon').textContent = data.icon;
            document.getElementById('era-title').textContent = data.title;
            document.getElementById('era-description').textContent = data.description;
            document.getElementById('era-insight').textContent = data.insight;
            document.getElementById('chart-title').textContent = data.chartTitle;
            document.getElementById('chart-caption').textContent = data.chartCaption;

            // 3. Populate Events List
            const eventsList = document.getElementById('era-events');
            eventsList.innerHTML = '';
            data.events.forEach(event => {
                const li = document.createElement('li');
                // *** Modification: Change from horizontal 'flex' to vertical 'flex flex-col' for stacked layout ***
                // เปลี่ยน li.className เป็น flex flex-col เพื่อจัดเรียงในแนวตั้ง และเอา gap-4 ออก
                li.className = "flex flex-col p-3 bg-gray-50 rounded shadow-sm border-l-4 border-[#D4A017]";
                li.innerHTML = `
                    <!-- *** Modification: Removed horizontal constraints, added mb-1 for spacing below the year *** -->
                    <span class="font-bold text-[#4A3B32] mb-1">${event.year}</span>
                    <span class="text-sm text-gray-700">${event.text}</span>
                `;
                eventsList.appendChild(li);
            });

            // 4. Render Chart
            // FIX: Pass data.chartConfig instead of undefined 'config'
            renderChart(data.chartConfig);
        }

        function renderChart(config) {
            const ctx = document.getElementById('mainChart').getContext('2d');
            
            if (currentChart) {
                currentChart.destroy();
            }

            // Common Chart Options for responsiveness and style
            const commonOptions = {
                responsive: true,
                maintainAspectRatio: false,
                plugins: {
                    legend: {
                        position: 'bottom',
                        labels: {
                            font: { family: 'Sarabun' }
                        }
                    },
                    tooltip: {
                        bodyFont: { family: 'Sarabun' },
                        titleFont: { family: 'Sarabun' }
                    }
                },
                scales: config.type === 'radar' ? {
                    r: {
                        ticks: { display: false },
                        pointLabels: { font: { family: 'Sarabun' } }
                    }
                } : {
                    y: {
                        beginAtZero: true,
                        grid: { color: '#E5E0D8' }
                    },
                    x: {
                        grid: { display: false }
                    }
                }
            };

            currentChart = new Chart(ctx, {
                type: config.type,
                data: {
                    labels: config.labels,
                    datasets: config.data
                },
                options: commonOptions
            });
        }

        // Initialize on load
        window.addEventListener('DOMContentLoaded', initApp);

    </script>
</body>
</html>

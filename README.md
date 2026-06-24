# CRAENP2
<html lang="th">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>EKG Decision Support Tool (OPQRST)</title>
    <!-- นำเข้า Tailwind CSS เพื่อความสวยงามและรองรับ Mobile Screen -->
    <script src="https://cdn.tailwindcss.com"></script>
</head>
<body class="bg-gray-50 text-gray-800 min-h-screen font-sans">

    <div class="max-w-md mx-auto bg-white min-h-screen shadow-lg flex flex-col justify-between">
        
        <!-- Header -->
        <header class="bg-red-600 text-white p-4 text-center shadow-md">
            <h1 class="text-xl font-bold tracking-wide">EKG Triage Supporter</h1>
            <p class="text-xs opacity-90 mt-1">ระบบช่วยตัดสินใจทำ EKG เบื้องต้นด้วยหลัก OPQRST</p>
        </header>

        <!-- Main Form -->
        <main class="p-4 flex-grow space-y-5 overflow-y-auto">
            
            <!-- Risk Factors Box -->
            <div class="bg-gray-100 p-3 rounded-lg border border-gray-200">
                <h2 class="text-sm font-bold text-gray-700 mb-2 uppercase tracking-wider">1. ประวัติเสี่ยง (Risk Factors)</h2>
                <div class="grid grid-cols-2 gap-2">
                    <label class="flex items-center space-x-2 text-sm bg-white p-2 rounded border cursor-pointer">
                        <input type="checkbox" id="risk_age" class="w-4 h-4 text-red-600">
                        <span>ชาย >= 45 / หญิง >= 55</span>
                    </label>
                    <label class="flex items-center space-x-2 text-sm bg-white p-2 rounded border cursor-pointer">
                        <input type="checkbox" id="risk_dm_htn" class="w-4 h-4 text-red-600">
                        <span>เบาหวาน / ความดัน / ไขมัน</span>
                    </label>
                    <label class="flex items-center space-x-2 text-sm bg-white p-2 rounded border cursor-pointer">
                        <input type="checkbox" id="risk_smoke" class="w-4 h-4 text-red-600">
                        <span>สูบบุหรี่ปัจจุบัน</span>
                    </label>
                    <label class="flex items-center space-x-2 text-sm bg-white p-2 rounded border cursor-pointer">
                        <input type="checkbox" id="risk_cad" class="w-4 h-4 text-red-600">
                        <span>เคยเป็นโรคหัวใจ/มีประวัติในบ้าน</span>
                    </label>
                </div>
            </div>

            <!-- OPQRST Section -->
            <div class="space-y-4">
                <h2 class="text-sm font-bold text-gray-700 uppercase tracking-wider">2. การประเมินอาการ (OPQRST)</h2>

                <!-- O: Onset -->
                <div class="space-y-1">
                    <label class="block text-sm font-semibold text-gray-700">O - Onset (การเกิดอาการ)</label>
                    <select id="onset" class="w-full p-2 border rounded-md bg-white focus:ring-2 focus:ring-red-500">
                        <option value="" disabled selected hidden>--- กรุณาเลือก ---</option>
                        <option value="2">เกิดขึ้นเฉียบพลันทันที (Sudden / Acute)</option>
                        <option value="0">ค่อยๆ เป็นมากขึ้นเรื่อยๆ (Gradual)</option>
                    </select>
                </div>

                <!-- P: Provocation / Palliation -->
                <div class="space-y-1">
                    <label class="block text-sm font-semibold text-gray-700">P - Provocation (สิ่งกระตุ้น/บรรเทา)</label>
                    <select id="provocation" class="w-full p-2 border rounded-md bg-white focus:ring-2 focus:ring-red-500">
                        <option value="" disabled selected hidden>--- กรุณาเลือก ---</option>
                        <option value="2">เจ็บแน่นขึ้นเมื่อออกแรง / อมยาใต้ลิ้นแล้วดีขึ้น</option>
                        <option value="1">อาการคงที่ ไม่ว่าจะทำอะไร</option>
                        <option value="0">เจ็บเฉพาะเวลาหายใจเข้าลึกๆ หรือเมื่อกด/เปลี่ยนท่า</option>
                    </select>
                </div>

                <!-- Q: Quality -->
                <div class="space-y-1">
                    <label class="block text-sm font-semibold text-gray-700">Q - Quality (ลักษณะอาการเจ็บ)</label>
                    <select id="quality" class="w-full p-2 border rounded-md bg-white focus:ring-2 focus:ring-red-500">
                        <option value="" disabled selected hidden>--- กรุณาเลือก ---</option>
                        <option value="2">แน่นอึดอัด เหมือนมีอะไรทับ/บีบรัด (Pressure/Squeezing)</option>
                        <option value="1">แสบร้อนกลางอก (Heartburn/Burning)</option>
                        <option value="0">เจ็บแปลบๆ เหมือนเข็มแทง (Sharp/Stabbing)</option>
                    </select>
                </div>

                <!-- R: Region / Radiation -->
                <div class="space-y-1">
                    <label class="block text-sm font-semibold text-gray-700">R - Region / Radiation (ตำแหน่งและการร้าว)</label>
                    <select id="radiation" class="w-full p-2 border rounded-md bg-white focus:ring-2 focus:ring-red-500">
                        <option value="" disabled selected hidden>--- กรุณาเลือก ---</option>
                        <option value="2">ร้าวไปกราม, ไหล่ซ้าย, แขนซ้าย หรือแขนทั้งสองข้าง</option>
                        <option value="1">ร้าวไปที่หลัง หรือบริเวณอื่น</option>
                        <option value="0">เจ็บอยู่กับที่ ไม่ร้าวไปไหนเลย</option>
                    </select>
                </div>

                <!-- S: Severity -->
                <div class="space-y-1">
                    <label class="block text-sm font-semibold text-gray-700">S - Severity (ความรุนแรง Pain Score)</label>
                    <select id="severity" class="w-full p-2 border rounded-md bg-white focus:ring-2 focus:ring-red-500">
                        <option value="" disabled selected hidden>--- กรุณาเลือก ---</option>
                        <option value="2">รุนแรงมาก (7 - 10 คะแนน) หรือเจ็บที่สุดในชีวิต</option>
                        <option value="1">ปานกลาง (4 - 6 คะแนน)</option>
                        <option value="0">เล็กน้อย (1 - 3 คะแนน)</option>
                    </select>
                </div>

                <!-- T: Time -->
                <div class="space-y-1">
                    <label class="block text-sm font-semibold text-gray-700">T - Time (ระยะเวลาที่เจ็บต่อเนื่อง)</label>
                    <select id="time" class="w-full p-2 border rounded-md bg-white focus:ring-2 focus:ring-red-500">
                        <option value="" disabled selected hidden>--- กรุณาเลือก ---</option>
                        <option value="2">เจ็บต่อเนื่องยาวนานมากกว่า 20 นาที</option>
                        <option value="1">เจ็บๆ หายๆ เป็นพักๆ (Intermittent)</option>
                        <option value="0">เป็นแค่ไม่กี่วินาทีแล้วหายสนิท</option>
                    </select>
                </div>
            </div>

            <!-- Action Button -->
            <button onclick="evaluateEKG()" class="w-full bg-red-600 hover:bg-red-700 text-white font-bold py-3 px-4 rounded-md transition duration-200 shadow shadow-red-300">
                ประมวลผลการตัดสินใจ
            </button>

            <!-- Result Display Block (Hidden by default) -->
            <div id="resultBox" class="hidden p-4 rounded-lg border-2 text-center transition-all duration-300">
                <h3 class="font-bold text-lg mb-1" id="resultTitle"></h3>
                <p class="text-sm font-medium mb-2" id="resultScore"></p>
                <p class="text-sm" id="resultAction"></p>
            </div>

        </main>

        <!-- Disclaimer Footer -->
        <footer class="bg-gray-800 text-gray-400 p-3 text-[10px] text-center border-t border-gray-700">
            <span class="font-bold text-gray-300">คำเตือนทางคลินิก:</span> แอปพลิเคชันนี้เป็นเพียงระบบช่วยตัดสินใจเบื้องต้นตามหลัก EBP ไม่สามารถทดแทนดุลยพินิจของแพทย์หรือพยาบาลวิชาชีพได้ หากคนไข้มีอาการวิกฤตช็อกหรือหมดสติ ให้เปิดระบบทางเดินหายใจและทำ EKG ทันทีโดยไม่ต้องรอคะแนน
        </footer>

    </div>

    <!-- Logic Script -->
    <script>
        function evaluateEKG() {
            // ดึงค่าจาก Dropdown แต่ละตัวมาเช็คก่อน
            const onsetVal = document.getElementById('onset').value;
            const provocationVal = document.getElementById('provocation').value;
            const qualityVal = document.getElementById('quality').value;
            const radiationVal = document.getElementById('radiation').value;
            const severityVal = document.getElementById('severity').value;
            const timeVal = document.getElementById('time').value;

            // ตรวจสอบว่าผู้ใช้เลือกครบทุกช่องหรือยัง (Validation)
            if (onsetVal === "" || provocationVal === "" || qualityVal === "" || radiationVal === "" || severityVal === "" || timeVal === "") {
                alert("⚠️ กรุณาประเมินอาการ OPQRST ให้ครบทุกช่องก่อนกดประมวลผลครับ");
                return; // หยุดการทำงานทันทีถ้ายังเลือกไม่ครบ
            }

            // คำนวณคะแนนพารามิเตอร์ OPQRST เมื่อเลือกครบแล้ว
            let score = 0;
            score += parseInt(onsetVal);
            score += parseInt(provocationVal);
            score += parseInt(qualityVal);
            score += parseInt(radiationVal);
            score += parseInt(severityVal);
            score += parseInt(timeVal);

            // ดึงคะแนนจากปัจจัยเสี่ยง (Risk Factors)
            let riskScore = 0;
            if(document.getElementById('risk_age').checked) riskScore += 0.5;
            if(document.getElementById('risk_dm_htn').checked) riskScore += 0.5;
            if(document.getElementById('risk_smoke').checked) riskScore += 0.5;
            if(document.getElementById('risk_cad').checked) riskScore += 0.5;
            
            let totalScore = score + riskScore;

            // กำหนดตัวแปรสำหรับแสดงผล
            const resultBox = document.getElementById('resultBox');
            const resultTitle = document.getElementById('resultTitle');
            const resultScore = document.getElementById('resultScore');
            const resultAction = document.getElementById('resultAction');

            // แสดงกล่องผลลัพธ์
            resultBox.classList.remove('hidden');

            // ตัดสินใจตามระดับคะแนน (Risk Stratification Logic)
            if (totalScore >= 7 || (parseInt(onsetVal) === 2 && parseInt(qualityVal) === 2)) {
                // HIGH RISK (สีแดง)
                resultBox.className = "p-4 rounded-lg border-2 text-center bg-red-50 border-red-500 text-red-900 animate-pulse";
                resultTitle.innerHTML = "🚨 ความเสี่ยงสูง (High Risk)";
                resultScore.innerHTML = "คะแนนประเมินอาการ: " + totalScore + " คะแนน";
                resultAction.innerHTML = "<strong>ข้อแนะนำ:</strong> ทำ 12-lead EKG ทันทีภายใน 10 นาที! ติด Monitor สัญญาณชีพ รายงานแพทย์ และเตรียมพร้อมสำหรับภาวะ ACS";
            } 
            else if (totalScore >= 4 && totalScore < 7) {
                // MODERATE RISK (สีเหลือง)
                resultBox.className = "p-4 rounded-lg border-2 text-center bg-yellow-50 border-yellow-500 text-yellow-900";
                resultTitle.innerHTML = "⚠️ ความเสี่ยงปานกลาง (Moderate Risk)";
                resultScore.innerHTML = "คะแนนประเมินอาการ: " + totalScore + " คะแนน";
                resultAction.innerHTML = "<strong>ข้อแนะนำ:</strong> พิจารณาทำ EKG โดยเร็ว, ซักประวัติอาการร่วมอื่นๆ (เช่น เหงื่อแตกท่วม, คลื่นไส้อาเจียน) และเฝ้าระวังอาการอย่างใกล้ชิด";
            } 
            else {
                // LOW RISK (สีเขียว)
                resultBox.className = "p-4 rounded-lg border-2 text-center bg-green-50 border-green-500 text-green-900";
                resultTitle.innerHTML = "✅ ความเสี่ยงต่ำ (Low Risk)";
                resultScore.innerHTML = "คะแนนประเมินอาการ: " + totalScore + " คะแนน";
                resultAction.innerHTML = "<strong>ข้อแนะนำ:</strong> โอกาสเกิดภาวะหัวใจขาดเลือดต่ำ แต่อย่าเพิ่งวางใจ ให้ตรวจซ้ำหรือทำ EKG หากอาการเปลี่ยนไป หรือคนไข้ยังมีอาการเจ็บต่อเนื่อง";
            }
            
            // เลื่อนหน้าจอลงมาให้เห็นผลลัพธ์
            resultBox.scrollIntoView({ behavior: 'smooth' });
        }
    </script>
</body>
</html>

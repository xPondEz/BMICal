Test Cases เหล่านี้ครอบคลุมการทดสอบทั้งหน่วย (Metric) และระบบ (Imperial), ค่าขอบเขตของประเภท BMI, และการทดสอบกรณีข้อผิดพลาด (Error Handling)

##  **Test Cases สำหรับ BMI Calculator**

| No. | ประเภทการทดสอบ | หน่วย | น้ำหนัก (Weight) | ส่วนสูง (Height) | BMI ที่คาดหวัง | สถานะที่คาดหวัง |
| :---- | :---- | :---- | :---- | :---- | :---- | :---- |
| 1 | **Metric \- Normal** | Metric | 70 kg | 1.75 m (175 cm) | 22.9 | Normal weight |
| 2 | **Metric \- Underweight** | Metric | 50 kg | 1.70 m (170 cm) | 17.3 | Underweight |
| 3 | **Metric \- Boundary (18.5)** | Metric | 53.5 kg | 1.70 m (170 cm) | 18.5 | Normal weight |
| 4 | **Metric \- Boundary (24.9)** | Metric | 71.9 kg | 1.70 m (170 cm) | 24.9 | Normal weight |
| 5 | **Metric \- Overweight** | Metric | 85 kg | 1.80 m (180 cm) | 26.2 | Overweight |
| 6 | **Metric \- Boundary (30.0)** | Metric | 86.4 kg | 1.70 m (170 cm) | 30.0 | Obese |
| 7 | **Metric \- Obese** | Metric | 100 kg | 1.65 m (165 cm) | 36.7 | Obese |
| 8 | **Imperial \- Normal** | Imperial | 150 lbs | 70 inches | \~21.5 | Normal weight |
| 9 | **Imperial \- Conversion** | Imperial | 100 lbs | 60 inches | \~19.5 | Normal weight |
| 10 | **Error Handling** | Metric | Empty/NaN | 175 cm | Alert (No BMI) | Alert (กรุณากรอกน้ำหนักและส่วนสูง) |

Export to Sheets

### **รายละเอียดการทดสอบเพิ่มเติม**

* **Test Case 1, 5, 7:** ทดสอบกรณีทั่วไปสำหรับแต่ละประเภท BMI ในหน่วย **Metric**  
  * **สูตร BMI:** BMI=Height(m)2Weight(kg)​  
* **Test Case 3, 4, 6:** ทดสอบ **ค่าขอบเขต (Boundary Values)** ที่โค้ดใช้ในการตัดสินสถานะ BMI เพื่อให้แน่ใจว่าเงื่อนไข `if (bmi < 18.5)`, `else if (bmi < 25)`, `else if (bmi < 30)` ทำงานอย่างถูกต้อง  
  * **3:** 18.5 ถูกจัดเป็น **Normal weight** (เพราะเงื่อนไขแรกคือ `< 18.5`)  
  * **4:** 24.9 ถูกจัดเป็น **Normal weight** (เพราะเงื่อนไขที่สองคือ `< 25`)  
  * **6:** 30.0 ถูกจัดเป็น **Obese** (เพราะเงื่อนไขที่สามคือ `< 30` และสุดท้ายคือ `else`)  
* **Test Case 8, 9:** ทดสอบการคำนวณในหน่วย **Imperial** เพื่อยืนยันว่าฟังก์ชันแปลงหน่วยทำงานได้อย่างถูกต้อง  
  * **Conversion:** Weight(kg)=Weight(lbs)×0.453592, Height(cm)=Height(inches)×2.54  
* **Test Case 10:** ทดสอบ **Error Handling** เพื่อให้แน่ใจว่ามีการแจ้งเตือนผู้ใช้เมื่อไม่ได้กรอกค่าที่จำเป็นตามเงื่อนไข `if (!weight || !height)` ในฟังก์ชัน `calculateBMI()`


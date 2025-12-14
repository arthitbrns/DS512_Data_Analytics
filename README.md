Credit Card Approval Analysis and Predictive Modeling

(การวิเคราะห์และการสร้างแบบจำลองคาดการณ์การอนุมัติบัตรเครดิต)

1. Introduction
	สถาบันการเงินอนุมัติ/ปฏิเสธการสมัครบัตรเครดิต โดยพิจารณาจากข้อมูลผู้สมัคร โดยกระบวนการพิจารณาอาจใช้เวลานานและขึ้นอยู่กับดุลยพินิจของนักวิเคราะห์สินเชื่อ ซึ่งอาจนำไปสู่ความเสี่ยงหรือการสูญเสียโอกาสทางธุรกิจ
การวิเคราะห์ปัจจัยที่สำคัญเพื่อค้นหาคุณลักษณะที่สำคัญของผู้สมัครมีความสัมพันธ์กับการอนุมัติมากที่สุด เพื่อลดความเสี่ยงทางการเงิน (อัตราการผิดนัดชำระหนี้ - Default Rate) และเพิ่มประสิทธิภาพในการดำเนินงาน (Operational Efficiency) ของฝ่ายอนุมัติสินเชื่อของธนาคารและสถาบันการเงิน (ฝ่ายบริหารความเสี่ยง, ฝ่ายการตลาด, ฝ่ายปฏิบัติการ) 

2. Problem Statement/Background
การวิเคราะห์ปัจจัยที่สำคัญเพื่อค้นหาคุณลักษณะที่สำคัญของผู้สมัครมีความสัมพันธ์กับการอนุมัติมากที่สุด เพื่อลดความเสี่ยงทางการเงิน (อัตราการผิดนัดชำระหนี้ - Default Rate) โดยสนใจในคุณลักษณะใดของผู้สมัคร (เช่น อายุ, รายได้, ประเภทงาน) ที่มีความสัมพันธ์กับการอนุมัติมากที่สุด และเหมาะสมที่จะอนุมัติสินเชื่อมากที่สุด โดยแนวทางการวิเคราะห์จะดำเนินตาม Data Analysis Framework ต่อไปนี้
 
<img width="825" height="424" alt="image" src="https://github.com/user-attachments/assets/300f5d51-e287-4f8f-8013-fa949a0d7c10" />
ภาพที่ 1 Data Analytic Framework

2. Data Analytics Methodology
2.1 Analytical Questions 
เพื่อค้นหาคุณลักษณะของผู้สมัคร (เช่น อายุ, รายได้, ประเภทงาน) ที่มีความสัมพันธ์กับการอนุมัติมากที่สุด และหากลุ่มลูกค้า (Segments) ที่มีความเสี่ยงสูง/ต่ำ ที่แตกต่างกันชัดเจน

2.2. Data Sources/Attributes
 	Kaggle Dataset: "Credit Card Approvals (Clean Data)" (ซึ่งจำลองมาจากข้อมูลการสมัครบัตรเครดิต) 
ข้อมูลในทางปฏิบัติ: ฐานข้อมูลภายในของธนาคาร/สถาบันการเงิน (ข้อมูลการสมัคร, ประวัติสินเชื่อ, ข้อมูลเครดิตบูโร)

 <img width="1050" height="297" alt="image" src="https://github.com/user-attachments/assets/b895e107-1171-4fdd-827d-76bcd7677a6a" />

ภาพที่ 2 ตัวอย่าง Data Set

<img width="1050" height="413" alt="image" src="https://github.com/user-attachments/assets/5c67f152-6c18-4e1a-bc9e-e1707f2d8458" />
 
ภาพที่ 3 ตัวอย่าง Data Dictionary

2.3 Data cleaning and preprocessing 
เนื่องจากเป็น "Clean Data" จะเน้นการตรวจสอบขั้นสุดท้าย การจัดการกับค่าที่หายไป (Missing Values) ที่ยังอาจมีอยู่
3. Analytics Methodology 
3.1 EDA techniques: การวิเคราะห์ความถี่และค่าสถิติเชิงพรรณนา เพื่อดูความสัมพันธ์ของแต่ละคุณลักษณะกับผลการอนุมัติ

<img width="1050" height="218" alt="image" src="https://github.com/user-attachments/assets/1521e48f-4050-41be-85f7-207641d8c6c0" />
 
ภาพที่ 4 สถิติเชิงพรรณนา (Descriptive Statistics)

 <img width="940" height="377" alt="image" src="https://github.com/user-attachments/assets/f9ce54da-aadf-4fd1-8ee0-115ff9a3f2ad" />

ภาพที่ 5 Pivot Table and Graph

3.2 Visualization strategy: Heatmap สำหรับ Correlation Matrix

<img width="940" height="695" alt="image" src="https://github.com/user-attachments/assets/8024d114-9707-473c-be97-0419f031bf2b" />

 ภาพที่ 6 Correlation Heatmap (แผนที่ความร้อนสหสัมพันธ์)
 
ค่าสัมประสิทธิ์สหสัมพันธ์แบบเพียร์สัน (Pearson Correlation) ที่มีค่า มากกว่า 0.3 (ทั้งค่าบวกและลบ) หมายความว่ามีความสัมพันธ์เชิงเส้นระหว่างตัวแปรทั้งสองในระดับ ปานกลางถึงค่อนข้างมาก โดยมีค่าดังนี้
Married and BankCustomer = 0.992
PriorDefault and Approved = 0.720
Employed and CreditScore = 0.571
Employed and Approved = 0.458
PriorDefault and Employed = 0.432
CreditScore and Approved = 0.406
Age and YearsEmployed = 0.391
PriorDefault and CreditScore = 0.380
YearsEmployed and PriorDefault = 0.346
YearsEmployed and Approved = 0.322
YearsEmployed and CreditScore = 0.322
ZipCode and StateName = 0.302

<img width="294" height="269" alt="image" src="https://github.com/user-attachments/assets/7687968c-af06-48c2-bbac-a363a4827a9e" />

ภาพที่ 7 ค่าสัมประสิทธิ์สหสัมพันธ์แบบเพียร์สัน (Pearson Correlation) ที่มีค่า มากกว่า 0.3

<img width="940" height="370" alt="image" src="https://github.com/user-attachments/assets/e0646b56-eddd-4cbc-b616-b99075c95681" />

ภาพที่ 8 ค่าสัมประสิทธิ์สหสัมพันธ์แบบเพียร์สัน (Pearson Correlation) ที่มีสัมพันธ์กับการอนุมัติสินเชื่อ

บทสรุปเชิงวิเคราะห์: ปัจจัยด้าน ประวัติความเสี่ยง (PriorDefault) และ ความมั่นคง (Employed, CreditScore, YearsEmployed) เป็นคุณลักษณะหลักที่ขับเคลื่อนผลการตัดสินใจอนุมัติบัตรเครดิต ซึ่งตอบคำถามเชิงวิเคราะห์ที่ว่า "คุณลักษณะใดของผู้สมัครมีความสัมพันธ์กับการอนุมัติมากที่สุด"

3.3 Segmentation approach: การจัดกลุ่มลูกค้าตามโปรไฟล์ความเสี่ยง (Risk Profiles)
การเปรียบเทียบ Credit Score (CreditScore) ระหว่างผู้ที่ได้รับการอนุมัติ (Approved=1) และผู้ที่ไม่ได้รับการอนุมัติ (Approved=0) สามารถทำ t-test ได้ เนื่องจาก CreditScore เป็นตัวแปรเชิงปริมาณ(Numerical/ Continuous) และเราต้องการเปรียบเทียบค่าเฉลี่ยของตัวแปรนี้ระหว่างสองกลุ่มอิสระ(Approved=1 และ Approved=0) การใช้ Independent Samples T-test (การทดสอบทีสำหรับกลุ่มตัวอย่างอิสระ) จึงเป็นวิธีที่เหมาะสมที่สุด

 <img width="940" height="382" alt="image" src="https://github.com/user-attachments/assets/c4136c4b-05b7-4a37-af2f-a014b08700a0" />

ภาพที่ 9 Independent Samples T-test
ผลจากการวิเคราะห์ความสัมพันธ์ของฟีเจอร์ (Correlation Analysis) เป็นไปตามสมมติฐานที่ว่ามีกลุ่มลูกค้า(Segments) ที่มีความเสี่ยงสูง/ต่ำ ที่แตกต่างกันชัดเจนหรือไม่ กล่าวโดยสรุปคือ ค่าเฉลี่ย Credit Score ของผู้ที่ได้รับการอนุมิติ แตกต่าง จากผู้ที่ไม่ได้รับการอนุมัติ

4. Findings and Business Insights
คุณลักษณะหลักที่ขับเคลื่อนผลการอนุมัติบัตรเครดิต (Feature Importance) คือ ปัจจัยด้าน ประวัติความเสี่ยง (PriorDefault) และ ความมั่นคง (Employed, CreditScore, YearsEmployed) โดยสามารถ ระบุกลุ่มลูกค้าที่มีความเสี่ยงสูง/ต่ำ ที่ชัดเจนได้โดย Credit Score ซึ่งเป็นปัจจัยขับเคลื่อนหลัก (Primary Driver) ในกระบวนการอนุมัติ ทำให้เกิดการแบ่งกลุ่มลูกค้าเป็นสองกลุ่มได้อย่างมีประสิทธิภาพ 
ดังนั้นแนวโน้มและรูปแบบคุณลักษณะของผู้สมัครที่ถูกอนุมัติ/ปฏิเสธ คือ ประวัติความเสี่ยง (PriorDefault) และ ความมั่นคง (Employed, CreditScore, YearsEmployed) เป็นคุณลักษณะหลักที่ขับเคลื่อนผลการตัดสินใจอนุมัติบัตรเครดิต ซึ่งตอบคำถามเชิงวิเคราะห์ที่ว่า "คุณลักษณะใดของผู้สมัครมีความสัมพันธ์กับการอนุมัติมากที่สุด"
จากการเปรียบเทียบ Credit Score (CreditScore) ระหว่างผู้ที่ได้รับการอนุมัติ (Approved=1) และผู้ที่ไม่ได้รับการอนุมัติ (Approved=0) ค่าเฉลี่ย Credit Score ของผู้ที่ได้รับการอนุมิติ แตกต่าง จากผู้ที่ไม่ได้รับการอนุมัติ ซึ่งตอบคำถามเชิงวิเคราะห์ที่ว่า “มีกลุ่มลูกค้า (Segments) ที่มีความเสี่ยงสูง/ต่ำ ที่แตกต่างกันชัดเจนหรือไม่”

5. Conclusion and Recommendation
จากการวิเคราะห์ที่กล่าวมา จะทำให้เราทราบถึงปัจจัยสำคัญที่นำมาวิเคราะห์การอนุมัติสินเชื่อที่เหมาะสม ทำให้ลดการเกิดหนี้เสีย (ลดความเสี่ยง) เนื่องจากมีความแม่นยำในการคัดกรองมากขึ้น และเพิ่มโอกาสในการอนุมัติลูกค้าที่มีคุณภาพเร็วขึ้น (เพิ่มกำไร) และผู้สมัครได้รับผลการตัดสินใจรวดเร็วขึ้น ทำให้ประสบการณ์การใช้บริการดีขึ้น



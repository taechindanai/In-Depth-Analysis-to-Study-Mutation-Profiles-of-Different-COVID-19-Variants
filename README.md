# In-Depth-Analysis-to-Study-Mutation-Profiles-of-Different-COVID-19-Variants

3.1 รวบรวมข้อมูล
บทที่ 3 วิธีการดําเนินงาน
ในขั้นตอนแรก คณะผู<จัดทําได<รวบรวมข<อมูลจีโนมและโปรตีนของผู<ปüวยทั่วโลกเพื่อนํามาใช<วิเคราะห. เพื่อให<สําเร็จตามวัตถุประสงค.ของโครงงานซึ่งทางคณะผู<จัดทําได<นําข<อมูลมาจาก NCBI (National Center for Biotechnology Information) โดยทําการเก็บข<อมูล ณ วันที่ 20 ธันวาคม พ.ศ. 2564
Figure 3.1 ภาพแสดงหน<าเว็บไซต.ฐานข<อมูล COVID-19 คณะผู<จัดทําได<รวบรวมในรูปแบบของไฟล. FASTA และนําข<อมูลที่ได<ไปใช<ในขั้นตอนตdอไป โดยรูปแบบ
ไฟล. FASTA
18
  Figure 3.2 แสดงถึงการอdานไฟล. FASTA ด<วย python
ไฟล. FASTA จะประกอบด<วยข<อมูล ID ชื่อ description และ รหัสของ sequence
3.2 การวิเคราะหข= Eอมูลเชิงสํารวจ
จากข<อมูลที่ได<จากขั้นตอนแรก กdอนที่จะนําไปใช<ในการเปรียบเทียบตําแหนdงของการกลายพันธุ.กับจีโนม อ<างอิงจะต<องทําการคัดกรองข<อมูลเพื่อให<การวิเคราะห.ในขั้นตอนตdอไปมีความเบี่ยงเบนน<อยที่สุด ซึ่งทางผู<จัดทําใช< การวิเคราะห.ข<อมูลเชิงสํารวจ (Exploratory Data Analysis: EDA) ของไวรัส COVID-19 โดยใช<ข<อมูลจาก NCBI VIRUS ซึ่งดูได<จาก [1]
แล<วนําข<อมูลจีโนมที่ได<ไปวิเคราะห.ผลในรูปแบบของแผนภูมิต<นไม< (Phylogenetic tree) โดยเลือกใช< จีโนมที่มีชdวงความยาวอยdางน<อย 29000 bp
3.3 การคํานวณ Shannon entropy
3.3.1 All Genome
กdอนที่จะคํานวณ Shannon entropy จะต<องทํา multiple sequence alignment (MSA) กับจีโนมที่ ต<องการศึกษาโดย คณะผู<จัดทําได<เลือกใช<ซอฟต.แวร. PANGOLIN ในการทํา multiple sequence alignment จากข<อมูลจีโนมทั้งหมดที่ได<จากการรวบรวมข<อมูล
หลังจากนั้นก็นําไฟล.ที่ได<จากการทํา multiple sequence alignment ไปคํานวณหา Shannon entropy แล<วจัดการกับข<อมูลที่ได<มาด<วย simple moving average (SMA) โดยที่ใช< window size = 15 แล<ว นําข<อมูลไป plot เปäนกราฟ
3.3.2 Genome associate with time
เพื่อศึกษาการเปลี่ยนแปลงของความแปรปรวนเทียบกับเวลา ทางคณะผู<จัดทําได<แบdงข<อมูลจีโนมที่ได< ออกมาเปäน 6 สdวนโดยแบdงตามเวลา แตdละสdวนจะมีระยะเวลา 4 เดือน แล<วนําแตdละสdวนไปทํา multiple sequence alignment โดยใช<ซอฟต.แวร. PANGOLIN หลังจากนั้นก็นําไฟล.ที่ได<จากการทํา multiple sequence alignment ไปคํานวณหา Shannon entropy แล<วนําข<อมูลที่ได<มาจัดการด<วย simple moving average (SMA) โดยที่ใช< window side = 15 และนําข<อมูลไป plot เปäนกราฟ จากนั้นนําข<อมูลที่ได<มาเปรียบเทียบกัน
3.3.3 Entropy of protein
ทางคณะผู<จัดทําได<เลือกโปรตีนที่จะนํามาศึกษาคือ ORF3a, ORF7a, ORF8a, ORF8 และ S protein นํา แตdละสdวนไปทํา multiple sequence alignment โดยใช<ซอฟต.แวร. PANGOLIN แล<วนําไฟล.ที่ได<จากการทํา multiple sequence alignment ไปคํานวณหา Shannon entropy โดยจะแบงd กลมdุ กรดอะมิโนออกเปäน 7 กลุdม ตามคุณสมบัติได<แกd (A,G,V), (C), (D,E), (F,I,L,P), (H,N,Q,W), (K,R), (M,S,T,Y)แล<ว ดึงข<อมูลรdวมกันตามหมวดหมูdเพื่อใช<คํานวณเอนโทรปë หลังจากนั้นจัดการทําข<อมูลที่ได<มาด<วย simple moving average (SMA) โดยที่ใช< window size = 15 จากนั้นนําข<อมูลไป plot เปäนกราฟแล<วนําข<อมูลได<มาไปใช<ตdอใน ขั้นตอนที่ 4
19
       
3.4 การระบายสีโปรตีน
ทางคณะผู<จัดทําได<ใช<ซอฟต.แวร. PyMOL ในการแสดงโมเดลของโปรตีน การระบายสีจะระบายความคdา Shannon entropy จากการคํานวณใน 3.3 ซึ่งทางคณะผู<จัดทําใช<ข<อมูลโมเดลโปรตีนจาก PDB (Protein Data Bank) โดย ORF3a ใช<โมเดล 6xdc และ S protein ใช<โมเดล 7sxr
โดยระบายสีโปรตีนโดยแบdงสีตาม region ของแตdละโปรตีนเพื่อนําไปวิเคราะห.ผลตdอไป
3.5 find identity percentage
20
ทางคณะผู<จัดทําได<คํานวณเปอร.เซ็นต.ความเหมือนของจีโนมเพื่อความสัมพันธ.การแพรdกระจายโรคจาก
สัตว. หรือจากมนุษย. โดย ทําการ pairwise alignmentครั้งละคูd DQ022305.2
, MG772934.1
, CRR122287,
NC_004718.3 นํามาจับคูdกับ NC_045512.2 โดยที่ DQ022305.2,MG772934.1
และ CRR122287 คือจีโนม
จากเชื้อไวรัสที่ระบาดในค<างคาวและNC_0047188คือจีโนมของSARSซึ่งจีโนมจากสอง intermidiate host ที่ ตdางกันเปäนจีโนมที่คาดวdามีความเกี่ยวข<องทางสายวิวัฒนาการและ NC_045512.2 ที่นํามาเปรียบเทียบคือคือจีโนม ของเชื้อไวรัส COVID-19 ที่ค<นพบครั้งแรกใน Wuhan ทางผู<จัดทําได<ใช<จีโนมนี้เปäนตัวอ<างอิงและตัวเปรียบเทียบ
เพราะเปäนจีโนมตัวแรกที่ถูกค<นพบ จึงนําไปคํานวณเปอร.เซ็นต.ความเหมือน
3.6 coevolutionary coupling proteins analysis
ทางคณะผู<จัดทําได<ทําการคํานวณคdา mutual information เพื่อศึกษา coevolution coupling และ แสดงคdาเปäน Heatmap โดยทํากับ S protein , ORF3a , ORF7a , ORF7b และ ORF8

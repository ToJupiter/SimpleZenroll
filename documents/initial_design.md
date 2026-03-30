# Description:
Our university is really big (around 100k students total) and is in its class registration system. Design and create a system that can handle 100k requests/second at its peak, following ACID compliance and provide a platform for data analytics (both OLAP and OLTP in one unified system).

# System requirements
1. Our suite will be PostgreSQL, FastAPI as the backend. We do not need things such as nginx, rate limiting or something. Or maybe we would use Caddy, but save that for last. Design us optimized SQL for PostgreSQL for it to work perfectly. Avoid using indexes.
2. We will be using Kafka and Redis. These two tools should be used carefully and tune carefully for both optimized write and read queries, because we have a big number of both. Every student has to register at least 5 and maximum of around 20 classes. They also need to read constant class data from our source of truth (class list in semester). 
3. We also have an Apache Spark platform for analytics, real-time and live data analytics. Huge live data is pouring in, leveraging the distributed nature of Spark at its peak. Every tool used should be highlighting its usefulness and its huge contribution as well as deep management and settings controlled in our environment.
4. While the tools used are diverse and sophisticated, keep the code design (git repo design and files) smallest while expandable. The reason is this is just a demo settings, every line of code should be taken care and our tools should be utilized to their best and as fittest as possible instead of creating too many excessive features but not having a significant contribution. We all run under Python, all of main components should be grouped, Dockerized and all triggered upon docker compose up.

# Metadata:
1. We will be giving you a sample of our class table, which lists all classes in our semester. Of course there are plenty of samples, and we should be getting more. But please list me the most important features in this table (day_of_week, class time, class_id, course_id, capacity, room, etc...) just the finesse of them:
``` xlsx
Kỳ	Trường_Viện_Khoa	Mã_lớp	Mã_lớp_kèm	Mã_HP	Tên_HP	Tên_HP_Tiếng_Anh	Khối_lượng	Ghi_chú	Buổi_số	Thứ	Thời_gian	1	3	Kíp	Tuần	Phòng	Cần_TN	SLĐK	SL_Max	Trạng_thái	Loại_lớp	Đợt_mở	Mã_QL	TeachingType
20252	TDDT	169991	169991	AC2030	Khai thác thông tin đa phương tiện	Multimedia Information Processing	2(2-1-0-4)	CN giáo dục - nhóm 1-K69S	1	6	0645-0910	1	3	Sáng	25-32,34-42	D9-503	NULL	36	50	Điều chỉnh ĐK	LT+BT	AB	CT CHUẨN	
20252	TDDT	169991	169991	AC2030	Khai thác thông tin đa phương tiện	Multimedia Information Processing	2(2-1-0-4)	CN giáo dục - nhóm 1-K69S	1	6	0645-0910	4	6	Sáng	25-32,34-42	D9-503	NULL	36	50	Điều chỉnh ĐK	LT+BT	AB	CT CHUẨN	
20252	TDDT	169992	169992	AC2030	Khai thác thông tin đa phương tiện	Multimedia Information Processing	2(2-1-0-4)	CN giáo dục - nhóm 2-K69S	1	6	0920-1145	4	6	Sáng	25-32,34-42	D9-504	NULL	50	50	Điều chỉnh ĐK	LT+BT	AB	CT CHUẨN	
20252	TDDT	168228	168228	AC2040E	Cở sở dữ liệu	Databases	2(2-1-0-4)	**CTTT-Đa phương tiện-K69C	1	6	1505-1730	4	6	Chiều	25-32,34-42	D8-302	NULL	36	55	Điều chỉnh ĐK	LT+BT	AB	ELITECH	
20252	TDDT	170001	170001	AC2050	Cấu trúc dữ liệu và giải thuật	Data Structure and Algorithm	2(2-1-0-4)	CN giáo dục-K69S	1	5	0920-1145	4	6	Sáng	25-32,34-42	D3-105	NULL	45	45	Điều chỉnh ĐK	LT+BT	AB	CT CHUẨN	
20252	TDDT	169993	169993	AC2060	Nhập môn trí tuệ nhân tạo	Introduction to Artificial Intelligence	2(2-1-0-4)	CN giáo dục - nhóm 1-K69S	1	6	0920-1145	1	3	Sáng	25-32,34-42	D9-503	NULL	51	55	Điều chỉnh ĐK	LT+BT	AB	CT CHUẨN	
20252	TDDT	169994	169994	AC2060	Nhập môn trí tuệ nhân tạo	Introduction to Artificial Intelligence	2(2-1-0-4)	CN giáo dục - nhóm 2-K69S	1	6	0645-0910	1	3	Sáng	25-32,34-42	D9-504	NULL	46	55	Điều chỉnh ĐK	LT+BT	AB	CT CHUẨN	
20252	TDDT	169995	169995	AC2070	Thiết kế và lập trình web	Web Design and Progamming	3(3-0-1-6)	CN giáo dục - nhóm 1-K69S	1	3	0645-0910	4	6	Sáng	25-32,34-42	D9-503	TN	56	55	Điều chỉnh ĐK	LT+BT	AB	CT CHUẨN	
```

2. For student's information, modest information only. No need excessive information (phone number, address, etc...), just the basic ones. 

# Steps:
1. Create a good SQL first to be used with the database. We create an object in Python to map to database. 
2. Design me the Git Repo directory tree with files, where are they located. The least code files as you possibly can. I do not want many of them, excessive is not good. Then, generate me the commands in Linux to generate the structure.
3. Start by generating the parts in this order: SQL -> kafka -> registration system backend -> analytics system -> deployment steps. Optimize the code generation for quick development process, MVP as fast as you can. The code generation should not have any comments except the function description comments. When touching the main components (Spark, Kafka, database, etc...) tune the params carefully and ask me questions in your explanation (your explanation outside of the code, ask as much as you can to kickstart my ability to critically think). Code must be clean, everything should be wonderful, but the description is full of questions for critical thinking.
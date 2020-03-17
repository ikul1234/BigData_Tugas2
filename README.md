# Tugas2_BigData_05111740000169
- [Tugas2_BigData_05111740000169](#tugas2bigdata05111740000169)
	- [1_DB](#1db)
		- [Exercise 01](#exercise-01)
			- [Full Workflow](#full-workflow)
		- [Exercise 02](#exercise-02)
			- [Nomor 1](#nomor-1)
			- [Nomor 2](#nomor-2)
			- [Nomor 3](#nomor-3)
			- [Nomor 4](#nomor-4)
			- [Full Workflow](#full-workflow-1)
		- [Exercise 03](#exercise-03)
			- [Nomor 1](#nomor-1-1)
			- [Nomor 2](#nomor-2-1)
			- [Full Workflow](#full-workflow-2)
		- [Exercise 04](#exercise-04)
			- [Nomor 1](#nomor-1-2)
			- [Nomor 2](#nomor-2-2)
			- [Full Workflow](#full-workflow-3)
	- [2_Hadoop](#2hadoop)
		- [Exercise 00](#exercise-00)
			- [Full Workflow](#full-workflow-4)
		- [Exercise 01](#exercise-01-1)
			- [Full Workflow](#full-workflow-5)
		- [Exercise 02](#exercise-02-1)
			- [Full Workflow](#full-workflow-6)
## 1_DB
### Exercise 01
* Pertama saya drag newCensus.sqlite dari folder Data
* Lalu buat DB Table Selector
* Di dalam DB Table Selector, pilih table yang bernama ss13pme
* SQL Statementnya SELECT * FROM #table#
* Lalu klik Apply dan OK
* Setelah itu buat DB Reader untuk mengimport data tersebut
#### Full Workflow

### Exercise 02
#### Nomor 1
* Pertama saya buat DB Joiner untuk join dua table tersebut
* Lalu dalam DB Joiner, pilih Inner Join dan kedua input table berisi serialno
* Setelah itu buat DB Column Filter yang isinya mengexclude puma* & pwgtp*
* Setelah itu buat DB Reader untuk mengimport data tersebut
#### Nomor 2
* Pertama buat DB Row Filter yang berisi condition cow is null
* Lalu buat DB Reader untuk mengimport data tersebut
#### Nomor 3
* Pertama buat DB Row Filter yang berisi condition cow is not null
* Lalu buat DB Reader untuk mengimport data tersebut
#### Nomor 4
* Pertama buat DB GroupBy
* Di dalam Group column(s) masukkan sex
* Lalu di manual Aggregation masukkan agep untuk AVG
* Masukkan juga agep untuk costum yang berisi function AVG(#COLUMN_NAME# + #SECOND_COLUMN_NAME#)
* Lalu buat DB Reader untuk mengimport data tersebut
#### Full Workflow

### Exercise 03
#### Nomor 1
* Pertama saya buat Decision Tree Learner 
* Lalu di dalam Decision Tree Learner ganti class columnnya menjadi cow
#### Nomor 2
* Pertama buat Decision Tree Predictor
* Lalu di dalam Decision Tree Predictor ganti prediction column namenya menjadi cow
#### Full Workflow

### Exercise 04
#### Nomor 1
* Pertama saya buat DB Connection Table Writer
* Lalu di dalam DB Connection Table Writer pilih table yang bernama ss13pme_original
* Lalu pilih Overwrite
#### Nomor 2
* Pertama buat DB Update dan sambungkan Decision Tree Predictor & SQLite Connector
* Di dalam DB Update pilih table ss13pme
* Yang atas masukkan cow
* Yang bawah masukkan serialno
#### Full Workflow

## 2_Hadoop
### Exercise 00
* Pertama saya ganti nama table dengan 05111740000169_(namafile) pada kedua DB Table Creator dan DB Loader
#### Full Workflow

### Exercise 01
* Pertama saya ganti SQLite Connector menjadi Create Local Big Data Environment dari exercise sebelumnya
* Lalu ganti table dengan 05111740000169_ss13pme pada DB Table Selector
#### Full Workflow


### Exercise 02
* Pertama ubah nama tabel pada DB Table Selector menjadi 05111740000169_ss13pme
* Lalu tambahkan DB Table Creator dengan koneksi dari hive dan concatenate
* Lalu ganti nama tabel dengan 05111740000169_newTable
* Lalu buat Create Temp Dir
* Di dalamnya uncheck create temp dir on workflow
* Lalu tambahkan string manipulation(Variable) dengan input Create Temp Dir sebelumnya
* Di dalamnya Buat expression menjadi replace(regexReplace($${Stemp_path}$$, "[A-Z]:" ,""), "\\", "/")
* Setelah itu buat DB Loader dengan input String Manipulation, DB Table Creator, Concatenate, dan Koneksi Hive
* Di dalamnya ganti nama tabel menjadi 05111740000169_newTable
#### Full Workflow

//part c:

1.  Questions:
       1-ينفع اعدل الحجز بعد تاريخ بدايتة واية الشروط SRS:Rental& Booking Management
       2- ينفع العميل الواحد يحجز اكتر من عربية في نفس الفترة بنفس السعر SRS:Customer Policies

2. Assumptions:
      1- أن حالة السيارة (Status) في جدول VEHICLE تتحدث تلقائياً بين (Available, Rented, Under Maintenance) بناءً على عمليات الحجز والصيانة SRS:Vehicle Fleet Operations
      2- تليفونات العملاء (CUSTOMER_PHONE) او الفروع (BRANCH_PHONE) يتم التعامل معها كأرقام متعددة القيم (Multivalued Attributes) ولها جداول مستقلة لضمان عدم حدوث تكرار في البيانات  SRS: Data Modeling & Schema Design


3 . Contradictions
SRS بين قسم Vehicle Fleet Operations  وقسم Maintenance Management
متوضحش ينفع صيانة سيارة محجوزة ولا لا 





//  Part D

1- SRS section:  Rental & Booking Management    
 Business rule: لا يمكن إنشاء حجز جديد لسيارة إذا كانت هذه السيارة محجوزة بالفعل أو في فترة صيانة متداخلة مع تواريخ الحجز الجديد (StartDate و EndDate).
 Why constraints are not enough: قيود الجداول العادية (PK, FK, CHECK) تفحص كل جدول على حدة ولا يمكنها مقارنة تواريخ الحجوزات المتعددة أو التحقق من التداخل الزمني عبر جدولين (BOOKING و VEHICLE/MAINTENANCE).
 How to enforce it: Database Trigger (أو Application Logic) يتم تنفيذه قبل عملية الـ INSERT على جدول BOOKING للتحقق من عدم وجود أي تقاطع في التواريخ لنفس السيارة.

2- SRS section: Vehicle Fleet Operations
 Business rule: يجب تحديث حالة السيارة (Status) تلقائياً إلى Rented عند تأكيد الحجز، وتصبح Under Maintenance أثناء فترة الصيانة، وAvailable عند انتهائها.
 Why constraints are not enough: القيود الثابتة مثل DEFAULT أو CHECK لا تستطيع تغيير قيم الأعمدة ديناميكياً بناءً على أحداث جدول آخر (مثل إنشاء حجز جديد أو تسجيل صيانة).
  How to enforce it: Database Triggers مرتبطة بجداول BOOKING و MAINTENANCE لتحديث عمود Status في جدول VEHICLE تلقائياً عند حدوث هذه العمليات.
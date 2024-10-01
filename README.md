класс MatrixFunc является примером разреженного (sparse) класса для хранения матриц, поскольку он экономно хранит только ненулевые элементы на диагоналях матрицы, игнорируя нулевые значения, которые занимают значительное место в памяти в традиционном подходе.

Объяснение концепции:
Разреженная матрица — это матрица, в которой большая часть элементов равна нулю. Для таких матриц целесообразно использовать специальные структуры данных, которые хранят только ненулевые значения, чтобы экономить память и ускорить операции.

Экономное представление:

В обычной полной матрице (Matrix) каждый элемент хранится независимо, даже если он равен нулю.
В MatrixFunc хранятся только ненулевые элементы, распределенные по диагоналям, что существенно сокращает использование памяти.
Преимущества разреженного хранения:
Экономия памяти: Вместо хранения полного массива элементов (включая нули) хранится только минимальный набор ненулевых элементов.
Ускорение операций: Операции над матрицами (например, сложение или умножение) могут выполняться быстрее, так как обрабатываются только ненулевые элементы.
Преобразование форматов: В данном случае мы можем легко преобразовать полную матрицу в разреженный формат и наоборот.
Пояснение к коду:
Класс Matrix хранит матрицу полностью, занимая память пропорционально числу строк и столбцов (O(n×m)).
Класс MatrixFunc хранит только ненулевые диагонали в виде std::map<int, std::vector<int>>, где:
int — индекс диагонали (например, главная диагональ — 0, верхняя диагональ — положительное значение, нижняя — отрицательное).
std::vector<int> — значения элементов на этой диагонали.
Операции доступа к элементам в MatrixFunc более сложные, так как нужно учитывать сдвиги для диагоналей, но это компенсируется уменьшенным объемом памяти.
Виды разреженных матриц:
Матрицы с диагональным представлением (как в данном примере).
Матрицы в формате CSR (Compressed Sparse Row) — используют три массива: значения, индексы строк и указатели на начало каждой строки.
Матрицы в формате COO (Coordinate Format) — хранятся только координаты ненулевых элементов и их значения.
Таким образом, MatrixFunc — это частный случай разреженной матрицы, предназначенный для экономного хранения матриц с ненулевыми диагоналями.







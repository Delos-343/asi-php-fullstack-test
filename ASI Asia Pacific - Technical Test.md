
1. Dalam eloquent (laravel) ORM, mengapa penting untuk menggunakan properti *$fillable*?
	
	a. Untuk memberikan default nilai pada kolom-kolom model.
	
	***b. Untuk memastikan bahwa hanya kolom-kolom tertentu yang dapat diisi melalui mass assignment.***
	
	c. Agar model dapat menyimpan nilai-nilai yang bersifat rahasia.
	
	d. Untuk memberikan batasan pada jumlah data yang dapat diambil dari database.
	
	e. Untuk mencegah redudansi insert


2. Manakah dari berikut ini yang bukan fitur *Redis* di Laravel?
	
	***a. Pub/Sub (Publisher/Subscriber).***
	
	b. Manajemen antrian pekerjaan.
	
	c. Penyimpanan file secara terdistribusi
	
	d. Caching variabel PHP secara langsung.
	
	e. Data json sementara secara langsung


3. Apa yang dimaksud dengan "Cross-Origin Resource Sharing" (CORS) dalam konteks RESTful API?
	
	a. Teknik enkripsi data untuk mengamankan komunikasi.
	
	***b. Mekanisme untuk membagi sumber daya antar domain.***
	
	c. Metode otentikasi klien untuk mengakses sumber daya.
	
	d. Format data standar untuk pertukaran pesan.
	
	e. Optimasi koneksi antar layanan server.


4. Apa itu "autoload" dalam konteks Composer?
	
	a. Proses menginstal dependensi.
	
	b. Mekanisme untuk muatan otomatis class PHP.
	
	c. Fitur untuk mematikan cache Composer.
	
	d. Langkah-langkah untuk menyusun file composer.json.
	
	***e. Semua jawaban benar***


* Untuk soal nomer 6 hingga 8, perhatikan kode berikut:

	class UserController extends Controller {
	
	 public function index ( ) {
	 
		 $users = User::all();
	
		 return response() -> json($users);
	 }
	
	 public function store (Request $request) {
		 $validatedData = $request->validate([
			 'name' => 'required|string|max:255',
			 'email' => 'required|email|unique:users|max:255',
			 'password' => 'required|string|min:6',
		 ]);
	
		 $user
			 = User::create($validatedData);
	
		 return response() -> json($user, 201);
	 }
	
	
	 public function show ($id) {
		 $user
			 = User::find($id);
		 if ($user) {
			 return response() -> json($user);
		 } else {
			 return response() -> json(['message' => 'User not found'], 404);
		 }
	 }
	}


6. Apa yang dilakukan metode ***store*** pada kode diatas?
	
	a. Menghapus pengguna dari basis data.
	
	***b. Menambahkan data pengguna baru ke dalam memory index.***
	
	c. Memperbarui informasi pengguna yang sudah ada.
	
	d. Mengambil data satu pengguna berdasarkan ID.
	
	e. Menambahkan pengguna baru ke dalam database berdasarkan input yang divalidasi.

7. Apa yang dihasilkan oleh metode ***show*** jika pengguna dengan ID yang diberikan tidak ditemukan?
	
	a. Respons JSON dengan data pengguna yang ditemukan.
	
	***b. Respons 404 dengan pesan 'User not found'.***
	
	c. Respons header kosong dengan kode 404 tanpa data pengguna.
	
	d. Respons 500 dengan pesan kesalahan server.
	
	e. Respons null dengan parameter http 404


8. Jika model ***user*** diatas tersedia, maka untuk mempersiapkan model tersebut dapat menggunakan perintah:
	
	a. use App\Models\User;
	
	***b. use \App\Models\User;***
	
	c. use App/Models/User;
	
	d. use App\User->load();
	
	e. use Models\User;


9. Apa arti karakter "+" dalam pola regex [a-zA-Z0-9._-]+?
	
	a. Karakter "+" menandakan bahwa setiap karakter khusus harus diulangi tepat satu kali.
	
	b. Karakter "+" menandakan bahwa setiap karakter khusus bersifat opsional.
	
	***c. Karakter "+" menandakan bahwa setiap karakter tersebut dapat diulangi lebih dari 1 kali.***
	
	d. Karakter "+" menandakan bahwa setiap karakter khusus bersifat eksklusif.
	
	e. Karakter "+" menandakan bahwa setiap karakter khusus bersifat sementara dan repetisi


10. preg_match("/^\+?[0-9]$/", $nomor)
	
	* Pada potongan kode diatas, maka bernilai TRUE jika isi dari variable nomor adalah:
	
	a. +123.456.789
	
	b. +1.2.3.4.5.6.7.8.9
	
	***c. 1.2.3.4.5.6.7.8.9***
	
	d. +1,2,3,4,5,6,7,8,9
	
	e. +123456789


* Untuk soal nomor 11, perhatikan potongan kode berikut:

	import React, { useState } from 'react';
	
	const Counter: React.FC = () => {
	
		const [count, setCount] = useState<number>(0);
		
		const increment = () => setCount(count + 1);
		
		return (
			<div>
				<h1>Count: {count}</h1>
				<button onClick={increment}>Increment</button>
			</div>
		);
	};
	
	export default Counter;


11. Pada baris 4, Apa yang terjadi jika kita menghapus tipe number pada penggunaan ***useState***, menjadi *const [count, setCount] = useState(0);*
	
	a. TypeScript akan memberikan error karena tidak ada tipe yang ditentukan
	
	***b. TypeScript akan secara otomatis mendeteksi tipe count sebagai number berdasarkan nilai awal 0***
	
	c. Kompiler TypeScript akan mengubah count menjadi tipe *any*
	
	d. Kompiler TypeScript akan memberikan peringatan bahwa tipe count adalah *any*
	
	e. useState tidak dapat bekerja tanpa tipe yang ditentukan dalam TypeScript


* Untuk soal nomor 12 hingga 14, perhatikan kode kompleks berikut:

	[
		import React, { useState, useEffect } from 'react';
		
		// Interface untuk props komponen
		interface Todo {
			id: number;
			text: string;
			completed: boolean;
		}
		
		interface TodoAppProps {
			initialTodos: Todo[];
		}
		
		const TodoApp: React.FC<TodoAppProps> = ({ initialTodos }) => {
		
			const [todos, setTodos] = useState<Todo[]>(initialTodos);
			
			const [newTodo, setNewTodo] = useState<string>('');
			
			useEffect(() => {
				console.log('Todos updated:', todos);
			}, [todos]);
			
			const handleAddTodo = () => {
				if (newTodo.trim()) {
					const newTodoObj: Todo = {
						id: Date.now(),
						text: newTodo,
						completed: false,
					};
					setTodos([...todos, newTodoObj]);
					setNewTodo('');
				}
			};
			
			const toggleTodoCompletion = (id: number) => {
			
				const updatedTodos = todos.map(
					todo => todo.id
						=== id ? { ...todo, completed: !todo.completed } : todo
				);
			
				setTodos(updatedTodos);
			};
			
			return (
				<div>
					<h1> Todo App </h1>
					<input
						type="text"
						value={newTodo}
						onChange={(e) => setNewTodo(e.target.value)}
						placeholder="Add new todo"
					/>
					<button onClick={handleAddTodo}>Add Todo</button>
					<ul>
						{todos.map(todo => (
						<li key={todo.id}>
							<span
								style={{ textDecoration: todo.completed ?
								'line-through' : 'none' }}
								onClick={() => toggleTodoCompletion(todo.id)}
						>									
								{todo.text}
							</span>
						</li>
						))}
					</ul>
				</div>
			);
		};
		
		export default TodoApp;
	]

12. Pada kode di atas, komponen ***TodoApp*** menggunakan ***useState*** untuk menyimpan list ***todos***. Apa tipe data yang diterima oleh ***useState*** pada baris 16 ?
	
	***a. Todo [ ]***
	
	b. string [ ]
	
	c. object [ ]
	
	d. any [ ]
	
	e. number [ ]


13. Dalam kode di atas, ***useEffect*** digunakan untuk melacak perubahan pada array ***todos***. Apa yang akan terjadi jika kita menghapus ***todos*** dari dependency array dalam ***useEffect*** pada baris 19 sampai 21?:
	
	a. useEffect tidak akan dipanggil sama sekali.
	
	***b. useEffect hanya akan dipanggil sekali setelah komponen dirender pertama kali***
	
	c. useEffect akan dipanggil setiap kali ada perubahan pada state atau props komponen.
	
	d. useEffect akan dipanggil setiap kali ada perubahan pada todos dan newTodo
	
	e. useEffect akan dipanggil tanpa mempedulikan perubahan pada state atau props.


14. Perhatikan baris 35 sampai 40. Apa yang terjadi jika kita memanggil ***toggleTodoCompletion*** dengan id yang tidak ada dalam array *todos*?
	
	***a. Array todos akan tetap tidak berubah.***
	
	b. Array todos akan terhapus
	
	c. Array todos akan menambah elemen baru dengan status completed menjadi true
	
	d. Array todos akan melempar error
	
	e. Status completed untuk semua todo akan berubah menjadi true


15. Bagaimana cara mengidentifikasi unik suatu objek di dalam bucket AWS S3?
	
	***a. Etag (Entity Tag)***
	
	b. Nama objek
	
	c. URL objek
	
	d. Domain region
	
	e. ID pengguna AWS


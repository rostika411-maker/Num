[index.html](https://github.com/user-attachments/files/33328013/index.html)<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Generator Prompt Soal Numerasi SMA (BSKAP 046 Complete)</title>
    <style>
        :root {
            --primary: #2563eb;
            --primary-hover: #1d4ed8;
            --bg: #f8fafc;
            --card-bg: #ffffff;
            --text: #1e293b;
            --border: #cbd5e1;
        }

        body {
            font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Helvetica, Arial, sans-serif;
            background-color: var(--bg);
            color: var(--text);
            margin: 0;
            padding: 15px;
        }

        .container {
            max-width: 800px;
            margin: 0 auto;
            background: var(--card-bg);
            padding: 20px;
            border-radius: 12px;
            box-shadow: 0 4px 6px -1px rgba(0, 0, 0, 0.1);
        }

        h1 {
            color: var(--primary);
            margin-top: 0;
            font-size: 1.3rem;
            text-align: center;
            border-bottom: 2px solid #e2e8f0;
            padding-bottom: 12px;
        }

        .form-grid {
            display: grid;
            grid-template-columns: 1fr;
            gap: 15px;
            margin-bottom: 20px;
        }

        @media (min-width: 600px) {
            .form-grid {
                grid-template-columns: 1fr 1fr;
            }
            .full-width-desktop {
                grid-column: span 2;
            }
        }

        .form-group {
            display: flex;
            flex-direction: column;
        }

        label {
            font-weight: 600;
            margin-bottom: 6px;
            font-size: 0.88rem;
        }

        select, input, textarea {
            padding: 10px;
            border: 1px solid var(--border);
            border-radius: 6px;
            font-size: 0.9rem;
            outline: none;
            box-sizing: border-box;
            width: 100%;
        }

        select:focus, input:focus, textarea:focus {
            border-color: var(--primary);
        }

        .checkbox-group {
            display: flex;
            flex-direction: column;
            gap: 8px;
            margin-top: 4px;
        }

        .checkbox-item {
            display: flex;
            align-items: center;
            gap: 8px;
            font-weight: normal;
            font-size: 0.9rem;
        }

        button.btn-generate {
            width: 100%;
            background-color: var(--primary);
            color: white;
            border: none;
            padding: 12px;
            font-size: 1rem;
            font-weight: bold;
            border-radius: 6px;
            cursor: pointer;
        }

        button.btn-generate:hover {
            background-color: var(--primary-hover);
        }

        .output-area {
            margin-top: 20px;
        }

        .output-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 8px;
        }

        textarea#promptOutput {
            height: 220px;
            background-color: #f1f5f9;
            font-family: monospace;
            font-size: 0.85rem;
            resize: vertical;
        }

        .btn-copy {
            background-color: #059669;
            color: white;
            border: none;
            padding: 8px 12px;
            border-radius: 4px;
            cursor: pointer;
            font-weight: 600;
            font-size: 0.85rem;
        }
    </style>
</head>
<body>

<div class="container">
    <h1>Generator Prompt Soal Numerasi SMA</h1>
    
    <div class="form-grid">
        <!-- Mata Pelajaran SMA -->
        <div class="form-group">
            <label for="mapel">Mata Pelajaran (SMA):</label>
            <select id="mapel" onchange="updateCP()">
                <optgroup label="Umum / Wajib">
                    <option value="PAI dan Budi Pekerti">PAI dan Budi Pekerti</option>
                    <option value="Pendidikan Pancasila">Pendidikan Pancasila</option>
                    <option value="Bahasa Indonesia">Bahasa Indonesia</option>
                    <option value="Bahasa Inggris">Bahasa Inggris</option>
                    <option value="Matematika (Wajib)">Matematika (Wajib)</option>
                    <option value="Sejarah">Sejarah</option>
                    <option value="PJOK">PJOK</option>
                    <option value="Seni Budaya & Seni Rupa">Seni Budaya & Seni Rupa</option>
                </optgroup>
                <optgroup label="Pilihan - MIPA">
                    <option value="Fisika">Fisika</option>
                    <option value="Kimia">Kimia</option>
                    <option value="Biologi">Biologi</option>
                    <option value="Informatika">Informatika</option>
                    <option value="Matematika Tingkat Lanjut">Matematika Tingkat Lanjut</option>
                </optgroup>
                <optgroup label="Pilihan - IPS & Bahasa">
                    <option value="Ekonomi">Ekonomi</option>
                    <option value="Sosiologi">Sosiologi</option>
                    <option value="Geografi">Geografi</option>
                    <option value="Bahasa Inggris Tingkat Lanjut">Bahasa Inggris Lanjut</option>
                </optgroup>
            </select>
        </div>

        <!-- Kelas / Fase -->
        <div class="form-group">
            <label for="kelas">Kelas / Fase:</label>
            <select id="kelas">
                <option value="Kelas 10 (Fase E)">Kelas 10 (Fase E)</option>
                <option value="Kelas 11 (Fase F)">Kelas 11 (Fase F)</option>
                <option value="Kelas 12 (Fase F)">Kelas 12 (Fase F)</option>
            </select>
        </div>

        <!-- Elemen / Konten CP BSKAP 046 -->
        <div class="form-group full-width-desktop">
            <label for="cpSelect">Elemen / Elemen CP Resmi (BSKAP No. 046):</label>
            <select id="cpSelect" onchange="updateTP()">
                <!-- Diisi otomatis berdasarkan Mapel -->
            </select>
            <input type="text" id="cpCustom" placeholder="Edit atau ketik CP kustom jika diperlukan..." style="margin-top: 6px;">
        </div>

        <!-- Tujuan Pembelajaran (TP) -->
        <div class="form-group full-width-desktop">
            <label for="tpSelect">Pilih Tujuan Pembelajaran (TP) Numerasi Terkait:</label>
            <select id="tpSelect" onchange="syncTP()">
                <!-- Diisi otomatis berdasarkan Elemen CP -->
            </select>
            <input type="text" id="tpCustom" placeholder="Edit atau ketik TP kustom jika diperlukan..." style="margin-top: 6px;">
        </div>

        <!-- Jumlah Soal -->
        <div class="form-group">
            <label for="jumlahSoal">Jumlah Soal Total:</label>
            <input type="number" id="jumlahSoal" value="5" min="1" max="20">
        </div>

        <!-- Jenis Soal -->
        <div class="form-group">
            <label>Bentuk Soal:</label>
            <div class="checkbox-group">
                <label class="checkbox-item"><input type="checkbox" id="pg" checked> Pilihan Ganda Sederhana</label>
                <label class="checkbox-item"><input type="checkbox" id="bs" checked> Benar / Salah</label>
                <label class="checkbox-item"><input type="checkbox" id="pgk" checked> PG Kompleks (Banyak Jawaban)</label>
            </div>
        </div>
    </div>

    <button class="btn-generate" onclick="generatePrompt()">Buat Prompt AI</button>

    <div class="output-area">
        <div class="output-header">
            <label for="promptOutput"><strong>Hasil Prompt (Siap di-copy ke ChatGPT/Gemini):</strong></label>
            <button class="btn-copy" onclick="copyPrompt()">Salin Prompt</button>
        </div>
        <textarea id="promptOutput" readonly placeholder="Klik 'Buat Prompt AI' di atas..."></textarea>
    </div>
</div>

<script>
    // Database Lengkap Seluruh Elemen CP BSKAP No. 046 & TP Numerasi SMA
    const databaseCP = {
        'PAI dan Budi Pekerti': [
            {
                cp: "Elemen Al-Qur'an dan Hadis: Menganalisis ayat Al-Qur'an dan Hadis tentang toleransi, etos kerja, ilmu pengetahuan, serta pengelolaan harta/muamalah.",
                tp: [
                    "Menganalisis data statistik persentase kepedulian sosial dan distribusi zakat/infak berdasarkan teks pendukung.",
                    "Menghitung proporsi pembagian harta waris (Mawaris) atau nisab zakat mal berdasarkan skenario data kuantitatif."
                ]
            },
            {
                cp: "Elemen Akidah: Menganalisis cabang-cabang iman (Syu'abul Iman), hakikat tauhid, dan dampaknya pada perilaku kuantitatif/sosial sehari-hari.",
                tp: [
                    "Menginterpretasi data grafik survei Indeks Kebahagiaan dan tingkat religiusitas dalam masyarakat."
                ]
            },
            {
                cp: "Elemen Fikih: Menganalisis ketentuan muamalah (asuransi syariah, perbankan syariah, pinjaman) serta hukum keluarga Islam.",
                tp: [
                    "Menghitung perbandingan marjin simpanan dan bagi hasil perbankan syariah vs konvensional dari tabel ilustrasi.",
                    "Menganalisis data simulasi pembiayaan syariah dan penghitungan bagi hasil (mudharabah/musyarakah)."
                ]
            },
            {
                cp: "Elemen Sejarah Peradaban Islam (SPI): Menganalisis rekam jejak perkembangan peradaban Islam, kontribusi ilmuwan, dan data historis keislaman.",
                tp: [
                    "Menganalisis data garis waktu (timeline) dan grafik populasi/kontribusi ilmuwan pada masa Keemasan Islam (Golden Age)."
                ]
            }
        ],
        'Pendidikan Pancasila': [
            {
                cp: "Elemen Pancasila: Menganalisis keterkaitan sila-sila Pancasila dan penerapan nilai-nilainya dalam kebijakan serta kehidupan bermasyarakat.",
                tp: [
                    "Menganalisis data statistik Indeks Perilaku Anti-Korupsi (IPAK) atau Indeks Demokrasi Indonesia (IDI).",
                    "Menginterpretasi data persentase partisipasi masyarakat dalam gotong royong dan kegiatan sosial."
                ]
            },
            {
                cp: "Elemen Undang-Undang Dasar 1945: Menganalisis periodisasi konstitusi, hak dan kewajiban warga negara, serta APBN/APBD.",
                tp: [
                    "Menghitung proporsi alokasi anggaran Pendidikan dan Kesehatan dalam data tabel APBN/APBD.",
                    "Menganalisis grafik tren pelanggaran hak dan pengingkaran kewajiban warga negara."
                ]
            },
            {
                cp: "Elemen Bhinneka Tunggal Ika: Menganalisis potensi konflik, harmoni keberagaman, serta demografi multikultural.",
                tp: [
                    "Menginterpretasi data tabel komposisi suku, agama, dan bahasa untuk mengukur Indeks Kerukunan Umat Beragama."
                ]
            },
            {
                cp: "Elemen NKRI: Menganalisis konsep sengketa wilayah, pertahanan kebangsaan, dan data kedaulatan NKRI.",
                tp: [
                    "Menganalisis data statistik pelanggaran batas wilayah laut dan indeks ketahanan nasional."
                ]
            }
        ],
        'Bahasa Indonesia': [
            {
                cp: "Elemen Membaca dan Memirsa: Mengevaluasi gagasan, pandangan, dan akurasi data fakta pada teks infografis, grafik, tabel, dan diagram.",
                tp: [
                    "Mengevaluasi kesesuaian antara narasi artikel dengan data grafik/tabel pendukung.",
                    "Mengidentifikasi tren data naik/turun dan menarik kesimpulan implisit dari infografis berita."
                ]
            },
            {
                cp: "Elemen Menulis: Menyajikan laporan hasil observasi, teks eksposisi, atau esai ilmiah berbasis data statistik aktual.",
                tp: [
                    "Menyusun kalimat interpretasi data kuantitatif yang tepat berdasarkan tabel statistik yang disediakan."
                ]
            }
        ],
        'Bahasa Inggris': [
            {
                cp: "Elemen Reading and Viewing: Menganalisis dan menyimpulkan informasi spesifik serta tren numerik dari teks expository, chart, dan diagram.",
                tp: [
                    "Menginterpretasikan persentase, tren kenaikan/penurunan (Describing Trends), dan perbandingan angka dari grafik berbahasa Inggris.",
                    "Menyimpulkan isi data tabel fakta/fakta statistik dalam bentuk pemahaman teks narasi."
                ]
            }
        ],
        'Matematika (Wajib)': [
            {
                cp: "Elemen Bilangan: Menggeneralisasi sifat-sifat operasi bilangan berpangkat (eksponen), bentuk akar, serta logaritma.",
                tp: [
                    "Memecahkan masalah pertumbuhan populasi/bunga majemuk investasi menggunakan fungsi eksponen.",
                    "Menghitung tingkat kebisingan (Desibel) atau skala magnitudo gempa dengan fungsi logaritma."
                ]
            },
            {
                cp: "Elemen Aljabar dan Fungsi: Memodelkan fenomena dengan sistem persamaan/pertidaksamaan linear, fungsi kuadrat, dan eksponensial.",
                tp: [
                    "Determinan nilai maksimum/keuntungan optimum pada masalah program linear dari grafik kendala.",
                    "Menganalisis titik puncak dan perpotongan fungsi kuadrat dalam skenario gerak parabola/produksi."
                ]
            },
            {
                cp: "Elemen Geometri & Trigonometri: Menyelesaikan masalah rasio trigonometri segitiga siku-siku dan posisi objek dalam ruang.",
                tp: [
                    "Menghitung tinggi objek/jarak antar titik menggunakan konsep klinometer dan aturan trigonometri."
                ]
            },
            {
                cp: "Elemen Analisis Data dan Peluang: Mengevaluasi penyajian data (histogram, boxplot), ukuran pemusatan/penyebaran, dan peluang bersyarat.",
                tp: [
                    "Menganalisis rata-rata, simpangan baku, dan persentil dari data kelompok pada laporan kasus nyata.",
                    "Menghitung peluang bersyarat dan frekuensi harapan dalam pengambilan keputusan bisnis/kesehatan."
                ]
            }
        ],
        'Fisika': [
            {
                cp: "Elemen Pemahaman Fisika - Kinematika & Dinamika: Menganalisis gerak lurus (GLB/GLBB), gerak melingkar, gerak parabola, serta Hukum Newton.",
                tp: [
                    "Menganalisis grafik v-t dan s-t untuk menentukan jarak tempuh dan percepatan kendaraan.",
                    "Menghitung resultan gaya dan percepatan sistem beban terhubung pulley dari tabel eksperimen."
                ]
            },
            {
                cp: "Elemen Pemahaman Fisika - Energi & Usaha: Menganalisis konsep usaha, hukum kekekalan energi, efisiensi daya, dan energi terbarukan.",
                tp: [
                    "Menghitung konsumsi energi kilowatt-hour (kWh) harian dan total biaya listrik rumah tangga.",
                    "Menganalisis grafik efisiensi daya output vs input pada sistem panel surya atau turbin angin."
                ]
            },
            {
                cp: "Elemen Pemahaman Fisika - Fluida & Termodinamika: Menganalisis fluida statis/dinamis, azas Kontinuitas, Bernoulli, dan gas ideal.",
                tp: [
                    "Menghitung laju aliran (debit) dan perbedaan tekanan fluida dalam sistem perpipaan terstruktur.",
                    "Menganalisis grafik p-V pada siklus mesin termodinamika untuk menentukan usaha/efisiensi."
                ]
            },
            {
                cp: "Elemen Pemahaman Fisika - Listrik & Magnet: Menganalisis rangkaian arus searah (DC), hukum Ohm, Kirchhoff, dan induksi elektromagnetik.",
                tp: [
                    "Menghitung kuat arus, tegangan, dan hambatan pengganti pada rangkaian campuran berbasis diagram data."
                ]
            }
        ],
        'Kimia': [
            {
                cp: "Elemen Pemahaman Kimia - Stoikiometri: Mengolah data massa, volume molar gas, dan konsentrasi larutan dalam reaksi kimia kuantitatif.",
                tp: [
                    "Menghitung massa produk reaksi dan menentukan pereaksi pembatas berdasarkan tabel data percobaan.",
                    "Mengukur konsentrasi molaritas dan molalitas sampel larutan dari pengukuran volume dan massa."
                ]
            },
            {
                cp: "Elemen Pemahaman Kimia - Termokimia & Kinetika: Menganalisis perubahan entalpi (ΔH), laju reaksi, orde reaksi, dan kesetimbangan.",
                tp: [
                    "Menghitung harga ΔH reaksi berdasarkan data kalorimeter dan diagram tingkat energi.",
                    "Menganalisis tabel konsentrasi vs waktu untuk menentukan laju reaksi dan orde reaksi."
                ]
            },
            {
                cp: "Elemen Pemahaman Kimia - Asam Basa & Titrasi: Menganalisis derajat keasaman (pH), larutan penyangga, hidrolisis, dan kurva titrasi.",
                tp: [
                    "Menghitung nilai pH larutan asam/basa/buffer berdasarkan konsentrasi dan data Ka/Kb.",
                    "Menganalisis data kurva titrasi kuantitatif untuk menghitung kadar sampel dalam uji laboratorium."
                ]
            }
        ],
        'Biologi': [
            {
                cp: "Elemen Keanekaragaman Hayati & Ekosistem: Menganalisis interaksi komponen ekosistem, piramida ekologi, dan kurva populasi.",
                tp: [
                    "Menganalisis grafik kurva pertumbuhan populasi (logistik/eksponensial) dan daya dukung lingkungan.",
                    "Menghitung Indeks Keanekaragaman Spesies (Shannon-Wiener) berdasarkan data sampel vegetasi."
                ]
            },
            {
                cp: "Elemen Bioproses Sel & Metabolisme: Menganalisis transpor membran, pembelahan sel, serta aktivitas enzim/respirasi seluler.",
                tp: [
                    "Menginterpretasi data grafik pengaruh suhu/pH terhadap laju reaksi aktivitas enzim katalase."
                ]
            },
            {
                cp: "Elemen Genetika & Pewarisan Sifat: Menganalisis pola-pola hereditas Mendel/Non-Mendel, penyimpangan, dan silsilah keluarga.",
                tp: [
                    "Menghitung rasio persentase dan probabilitas fenotipe keturunan pada diagram persilangan genetika.",
                    "Menganalisis data penderita kelainan genetik dari peta silsilah keluarga (pedigree diagram)."
                ]
            }
        ],
        'Ekonomi': [
            {
                cp: "Elemen Mekanisme Pasar: Menganalisis fungsi permintaan dan penawaran, koefisien elastisitas, serta titik keseimbangan pasar.",
                tp: [
                    "Menghitung harga dan kuantitas keseimbangan pasar (Ekuilibrium) dari tabel/persamaan permintaan-penawaran.",
                    "Menghitung koefisien elastisitas harga permintaan berdasarkan tabel perubahan harga dan jumlah barang."
                ]
            },
            {
                cp: "Elemen Ekonomi Makro & Kebijakan: Menganalisis data pendapatan nasional (PDB), indeks harga konsumen, inflasi, dan APBN.",
                tp: [
                    "Menghitung Laju Inflasi dan Indeks Harga Konsumen (IHK) berdasarkan tabel harga komoditas utama.",
                    "Menganalisis data PDB dan Pendapatan Per Kapita untuk menentukan laju pertumbuhan ekonomi."
                ]
            },
            {
                cp: "Elemen Akuntansi Dasar: Menganalisis tahapan siklus akuntansi perusahaan jasa/dagang dan laporan keuangan.",
                tp: [
                    "Menghitung Laba/Rugi bersih dan Perubahan Modal berdasarkan data Laporan Keuangan sederhana."
                ]
            }
        ],
        'Sosiologi': [
            {
                cp: "Elemen Penelitian Sosial Kuantitatif: Mengolah, menguji, dan menyimpulkan data hasil survei, kuesioner, dan statistik sosial.",
                tp: [
                    "Menganalisis data tabel frekuensi survei tingkat ketimpangan sosial atau kemiskinan masyarakat.",
                    "Menginterpretasi data grafik Indeks Pembangunan Manusia (IPM) dan rasio Gini."
                ]
            },
            {
                cp: "Elemen Kelompok & Masalah Sosial: Menganalisis pembentukan kelompok sosial, eksklusi, ketimpangan, dan mobilitas sosial.",
                tp: [
                    "Menginterpretasi data persentase mobilitas sosial vertikal/horisontal berdasarkan sampel data demografi."
                ]
            }
        ],
        'Geografi': [
            {
                cp: "Elemen Kependudukan (Demografi): Menganalisis dinamika kependudukan, angka kelahiran/kematian, migrasi, dan piramida penduduk.",
                tp: [
                    "Menghitung Angka Ketergantungan (Dependency Ratio) dan Kepadatan Penduduk aritmatika/agraris.",
                    "Memproyeksikan jumlah penduduk beberapa tahun mendatang menggunakan rumus proyeksi geometris."
                ]
            },
            {
                cp: "Elemen Peta & Geospasial: Menganalisis peta topografi, penggunaan lahan, Sistem Informasi Geografis (SIG), dan skala.",
                tp: [
                    "Menghitung Kontur Interval (CI), skala peta kontur, serta titik ketinggian lokasi pada peta rupa bumi.",
                    "Menghitung titik henti (Break-even Location) interaksi spasial antara dua wilayah pemukiman."
                ]
            },
            {
                cp: "Elemen Iklim & Kebencanaan: Menganalisis data curah hujan, klasifikasi iklim (Junghuhn/Schmidt-Ferguson), serta mitigasi.",
                tp: [
                    "Menghitung tipe iklim berdasarkan tabel data curah hujan bulanan (bulan kering vs bulan basah)."
                ]
            }
        ],
        'Sejarah': [
            {
                cp: "Elemen Penelitian Historis Berbasis Data: Menganalisis peristiwa sejarah menggunakan bukti arsip, data kependudukan historis, dan ekonomi masa lalu.",
                tp: [
                    "Menganalisis data statistik ekspor-impor atau produksi rempah-rempah pada masa kolonial (VOC/Hindia Belanda).",
                    "Menginterpretasi grafik pertumbuhan populasi atau dampak statistik peristiwa historis tertentu."
                ]
            }
        ],
        'Informatika': [
            {
                cp: "Elemen Analisis Data (AD): Mengoleksi, membersihkan, mengolah, menganalisis, dan memvisualisasikan data bervolume besar.",
                tp: [
                    "Menganalisis dataset numerik menggunakan fungsi pengolahan data (Mean, Median, Filtering) pada spreadsheet.",
                    "Menginterpretasi visualisasi data chart/graph untuk mendukung pengambilan keputusan kuantitatif."
                ]
            },
            {
                cp: "Elemen Algoritma & Pemrograman: Menganalisis kompleksitas algoritma, struktur data terurut, dan perhitungan logika.",
                tp: [
                    "Menghitung langkah efisiensi waktu/memori (Big-O Notation) dari sebuah skema algoritma."
                ]
            }
        ],
        'PJOK': [
            {
                cp: "Elemen Kebugaran Jasmani: Menganalisis konsep, pengukuran, dan hasil evaluasi kebugaran jasmani berbasis data fisik.",
                tp: [
                    "Menghitung nilai Indeks Massa Tubuh (IMT) dan mengelompokkan kategori kebugaran berdasarkan tabel norma.",
                    "Menghitung Denyut Nadi Maksimal (DNM) dan Zona Latihan (Target Heart Rate) untuk program aktivitas fisik."
                ]
            },
            {
                cp: "Elemen Keterampilan Gerak & Olahraga: Menganalisis pencapaian rekor, jarak, statistik pertandingan, dan analisis biomekanika.",
                tp: [
                    "Menganalisis data statistik persentase keberhasilan tembakan/efisiensi taktik dalam pertandingan tim."
                ]
            }
        ],
        'Seni Budaya & Seni Rupa': [
            {
                cp: "Elemen Penilaian & Apresiasi Seni: Menganalisis karya seni rupa/musik berdasarkan proporsi, garis skala, frekuensi nada, dan estetika terukur.",
                tp: [
                    "Menghitung proporsi dan skala pembanding grid dalam pembuatan ulang karya seni rupa.",
                    "Menganalisis data frekuensi gelombang nada akustik atau rasio emas (Golden Ratio) dalam seni visual."
                ]
            }
        ]
    };

    const defaultContent = [
        {
            cp: "Analisis Data & Pemecahan Masalah Kuantitatif sesuai standar BSKAP 046.",
            tp: ["Memecahkan masalah kontekstual mata pelajaran berdasarkan analisis data tabel/grafik."]
        }
    ];

    function updateCP() {
        const mapel = document.getElementById('mapel').value;
        const cpSelect = document.getElementById('cpSelect');
        cpSelect.innerHTML = '';

        const listCP = databaseCP[mapel] || defaultContent;

        listCP.forEach((item, index) => {
            let opt = document.createElement('option');
            opt.value = index;
            opt.textContent = item.cp;
            cpSelect.appendChild(opt);
        });

        updateTP();
    }

    function updateTP() {
        const mapel = document.getElementById('mapel').value;
        const cpIndex = document.getElementById('cpSelect').value;
        const tpSelect = document.getElementById('tpSelect');
        tpSelect.innerHTML = '';

        const listCP = databaseCP[mapel] || defaultContent;
        const selectedCPObj = listCP[cpIndex] || listCP[0];

        // Tampilkan teks CP pada input manual
        document.getElementById('cpCustom').value = selectedCPObj.cp;

        // Tampilkan daftar opsi TP
        selectedCPObj.tp.forEach(tpText => {
            let opt = document.createElement('option');
            opt.value = tpText;
            opt.textContent = tpText;
            tpSelect.appendChild(opt);
        });

        syncTP();
    }

    function syncTP() {
        document.getElementById('tpCustom').value = document.getElementById('tpSelect').value;
    }

    function generatePrompt() {
        const mapel = document.getElementById('mapel').value;
        const kelas = document.getElementById('kelas').value;
        const jumlahSoal = document.getElementById('jumlahSoal').value;
        
        const cp = document.getElementById('cpCustom').value || document.getElementById('cpSelect').selectedOptions[0].text;
        const tp = document.getElementById('tpCustom').value || document.getElementById('tpSelect').value;

        let jenisSoal = [];
        if (document.getElementById('pg').checked) jenisSoal.push("Pilihan Ganda Sederhana (1 jawaban benar)");
        if (document.getElementById('bs').checked) jenisSoal.push("Benar / Salah (dengan 3-4 pernyataan terstruktur)");
        if (document.getElementById('pgk').checked) jenisSoal.push("Pilihan Ganda Kompleks (Banyak Jawaban/Centang pilihan)");

        if (jenisSoal.length === 0) {
            alert("Harap pilih minimal satu bentuk soal!");
            return;
        }

        const promptText = `Anda adalah seorang Pakar Pembuat Soal Numerasi dan Pengembang Kurikulum Merdeka Jenjang SMA.

Tolong buatkan paket soal numerasi kontekstual berdasarkan data berikut:

### **DATA UTAMA:**
- **Mata Pelajaran:** ${mapel}
- **Jenjang & Kelas:** SMA / ${kelas}
- **Konten / Elemen CP (BSKAP No. 046):** "${cp}"
- **Tujuan Pembelajaran (TP):** "${tp}"
- **Jumlah Soal:** ${jumlahSoal} soal

### **BENTUK SOAL YANG DIPERLUKAN:**
${jenisSoal.map(j => `- ${j}`).join('\n')}

---

### **PANDUAN PENYUSUNAN SOAL NUMERASI SMA:**
1. **Stimulus Data Kontekstual:** Setiap soal WAJIB memiliki stimulus berupa data nyata (seperti tabel angka, grafik/diagram, infografis, atau skenario kuantitatif).
2. **Level Kognitif Numerasi:** Proporsikan soal mencakup level Pemahaman (L1), Aplikasi (L2), dan Penalaran/HOTS (L3).
3. **Pilihan Ganda Kompleks:** Sertakan instruksi yang jelas (contoh: "Pilihlah dua atau tiga pernyataan yang tepat").
4. **Benar/Salah:** Sediakan 3-4 statement turunan langsung dari stimulus data.

---

### **OUTPUT YANG DIHARAPKAN:**
1. **Daftar Soal** (lengkap dengan stimulus data dan opsi).
2. **Kunci Jawaban**.
3. **Pembahasan Lengkap & Langkah Perhitungan Numerasi**.
4. **Pemetaan Indikator Soal & Level Kognitif (L1/L2/L3)**.

Silakan hasilkan soal yang akurat, rasional, dan kontekstual.`;

        document.getElementById('promptOutput').value = promptText;
    }

    function copyPrompt() {
        const copyText = document.getElementById('promptOutput');
        if(!copyText.value) {
            alert("Belum ada prompt yang dibuat!");
            return;
        }
        copyText.select();
        copyText.setSelectionRange(0, 99999);
        navigator.clipboard.writeText(copyText.value);
        alert("Prompt berhasil disalin ke clipboard!");
    }

    // Load inisialisasi awal
    window.onload = function() {
        updateCP();
    };
</script>

</body>
</html>

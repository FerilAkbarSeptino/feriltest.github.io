import React, { useState, useEffect, useMemo } from 'react';
import { 
  ShieldCheck, 
  ChevronRight, 
  ShoppingCart, 
  User, 
  Search, 
  CheckCircle2, 
  AlertCircle,
  Menu,
  X,
  Lock,
  Mail,
  ArrowRight,
  SearchX,
  Home
} from 'lucide-react';

// --- Theme Constants ---
const COLORS = {
  spoonBlue: '#00529B',
  spoonYellow: '#FFD700',
  racingWhite: '#F8F9FA',
  carbonGrey: '#212529',
};

// --- Mock Data ---
const PRODUCTS = [
  {
    id: 1,
    name: 'Spoon SW388 Wheel',
    category: 'Wheels',
    price: 'Rp 45.000.000',
    image: 'https://cdn.renderhub.com/impulse99/spoon-sports-sw388/spoon-sports-sw388-01.jpg',
    description: 'The legendary lightweight forged wheel for maximum performance.',
    specs: '15x6.5J, 4x100, +45'
  },
  {
    id: 2,
    name: 'Monoblock Caliper Set',
    category: 'Brakes',
    price: 'Rp 28.500.000',
    image: 'https://image.nengun.com/catalogue/1024x768/nengun-1300-6681-02-spoon-monoblock_caliper_set-a608aee3.jpg',
    description: 'High rigidity aluminum monoblock for consistent braking feel.',
    specs: '4-Pot, NISSIN OEM'
  },
  {
    id: 3,
    name: 'Carbon Bonnet (Type R)',
    category: 'Aero',
    price: 'Rp 32.000.000',
    image: 'https://jhpusa.com/cdn/shop/files/Spoon-Carbon-Bonnet-Vent-_FL5_-1.jpg?v=1718836890&width=1100',
    description: 'Weight reduction and engine bay cooling optimization.',
    specs: 'Dry Carbon Fiber'
  },
  {
    id: 4,
    name: 'N1 Muffler Kit',
    category: 'Engine',
    price: 'Rp 12.500.000',
    image: 'https://spoonusa.com/media/catalog/product/cache/a87677397e462feae9d1f1d5d0e96487/1/8/18000-fl1-000_00.jpg',
    description: 'Optimized exhaust flow with the signature Spoon race sound.',
    specs: 'SUS304 Stainless Steel'
  },
  {
    id: 5,
    name: 'Rigid Collar Kit',
    category: 'Suspension',
    price: 'Rp 4.200.000',
    image: 'https://spoonusa.com/media/catalog/product/cache/a87677397e462feae9d1f1d5d0e96487/s/p/sp-50261-fk8-000_00-8031.jpg',
    description: 'Improves chassis rigidity by eliminating subframe play.',
    specs: 'Special Aluminum Alloy'
  },
  {
    id: 6,
    name: 'Yellow Valve Cover',
    category: 'Engine',
    price: 'Rp 6.800.000',
    image: 'https://www.jdmyard.com/assets/full/12310-16B-000.jpg?20200817144812',
    description: 'The iconic Spoon yellow finish for your K-Series or B-Series engine.',
    specs: 'OEM Fitment'
  }
];

const CAR_MODELS = ['Civic EG', 'Civic EK', 'Civic FD2', 'Integra DC2', 'Integra DC5', 'S2000'];

// --- Components ---

const Navbar = ({ onOpenLogin, searchQuery, setSearchQuery, onGoHome }) => {
  const [showSearch, setShowSearch] = useState(false);

  return (
    <nav className="bg-white border-b border-gray-200 sticky top-0 z-50">
      <div className="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
        <div className="flex justify-between h-16 items-center">
          <div className="flex items-center gap-2">
            {/* Logo sekarang berfungsi sebagai tombol Home */}
            <div 
              onClick={onGoHome}
              className="bg-[#00529B] text-white font-black px-3 py-1 italic tracking-tighter text-xl cursor-pointer hover:bg-blue-800 transition-colors"
            >
              SPOON <span className="text-[#FFD700]">SPORTS</span>
            </div>
          </div>
          
          <div className="hidden lg:flex space-x-8 text-sm font-bold uppercase tracking-widest text-[#212529]">
            <button onClick={onGoHome} className="hover:text-[#00529B]">Beranda</button>
            <a href="#products" className="hover:text-[#00529B]">Produk</a>
            <a href="#compatibility" className="hover:text-[#00529B]">Kompatibilitas</a>
          </div>

          <div className="flex items-center space-x-4">
            <div className={`relative flex items-center transition-all duration-300 ${showSearch || searchQuery ? 'w-48 md:w-64' : 'w-10'}`}>
              <Search 
                size={20} 
                className="text-gray-500 cursor-pointer absolute left-2 z-10" 
                onClick={() => setShowSearch(!showSearch)}
              />
              <input 
                type="text"
                placeholder="Cari part..."
                value={searchQuery}
                onChange={(e) => setSearchQuery(e.target.value)}
                className={`pl-10 pr-4 py-2 bg-gray-100 border-none rounded-full text-sm outline-none w-full transition-opacity ${(showSearch || searchQuery) ? 'opacity-100' : 'opacity-0 pointer-events-none'}`}
              />
              {(showSearch || searchQuery) && searchQuery && (
                <X 
                  size={14} 
                  className="absolute right-3 text-gray-400 cursor-pointer hover:text-red-500" 
                  onClick={() => setSearchQuery('')}
                />
              )}
            </div>
            
            <ShoppingCart size={20} className="text-gray-500 cursor-pointer" />
            <button 
              onClick={onOpenLogin}
              className="flex items-center gap-2 bg-[#00529B] text-white px-4 py-2 rounded-sm text-sm font-bold"
            >
              <User size={16} /> LOGIN
            </button>
          </div>
        </div>
      </div>
    </nav>
  );
};

const CompatibilityChecker = () => {
  const [selectedModel, setSelectedModel] = useState('');
  const [status, setStatus] = useState(null);

  const checkStatus = () => {
    if (!selectedModel) return;
    setStatus('checking');
    setTimeout(() => setStatus('compatible'), 1000);
  };

  return (
    <section id="compatibility" className="scroll-mt-20">
      <div className="bg-[#212529] text-white p-8 rounded-lg shadow-xl mb-12 border-l-4 border-[#FFD700]">
        <h3 className="text-xl font-bold mb-4 flex items-center gap-2 italic">
          <ShieldCheck className="text-[#FFD700]" /> COMPATIBILITY CHECKER
        </h3>
        <p className="text-gray-400 text-sm mb-6">Pastikan suku cadang ini sesuai dengan spesifikasi kendaraan Anda.</p>
        
        <div className="flex flex-col md:flex-row gap-4">
          <select 
            className="flex-1 bg-gray-800 border border-gray-700 p-3 rounded text-white"
            value={selectedModel}
            onChange={(e) => setSelectedModel(e.target.value)}
          >
            <option value="">Pilih Model Mobil...</option>
            {CAR_MODELS.map(m => <option key={m} value={m}>{m}</option>)}
          </select>
          
          <button 
            onClick={checkStatus}
            className="bg-[#FFD700] text-black font-black px-8 py-3 rounded hover:bg-yellow-400 transition-colors uppercase italic"
          >
            Check Fitment
          </button>
        </div>

        {status === 'checking' && (
          <div className="mt-4 text-blue-400 animate-pulse flex items-center gap-2">
            Menganalisis basis data teknis...
          </div>
        )}

        {status === 'compatible' && (
          <div className="mt-4 p-3 bg-green-900/30 border border-green-500 text-green-400 rounded flex items-center gap-2">
            <CheckCircle2 size={18} /> Part ini 100% kompatibel dengan <strong>{selectedModel}</strong>.
          </div>
        )}
      </div>
    </section>
  );
};

const AuthModal = ({ isOpen, onClose }) => {
  if (!isOpen) return null;
  return (
    <div className="fixed inset-0 bg-black/80 flex items-center justify-center z-[100] p-4">
      <div className="bg-white w-full max-w-md rounded-lg overflow-hidden relative shadow-2xl">
        <button onClick={onClose} className="absolute top-4 right-4 text-gray-500 hover:text-black">
          <X size={24} />
        </button>
        
        <div className="bg-[#00529B] p-8 text-white">
          <h2 className="text-2xl font-black italic tracking-tighter mb-2">ACCESS PERFORMANCE</h2>
          <p className="text-blue-100 text-sm">Masuk ke akun Spoon Performance Anda.</p>
        </div>

        <form className="p-8 space-y-4" onSubmit={(e) => e.preventDefault()}>
          <div>
            <label className="block text-xs font-bold text-gray-500 mb-1 uppercase tracking-tighter">Alamat Email</label>
            <div className="relative">
              <Mail className="absolute left-3 top-3 text-gray-400" size={18} />
              <input 
                type="email" 
                placeholder="driver@performance.com"
                className="w-full pl-10 pr-4 py-3 border border-gray-200 rounded focus:border-[#00529B] outline-none"
              />
            </div>
          </div>

          <div>
            <label className="block text-xs font-bold text-gray-500 mb-1 uppercase tracking-tighter">Kata Sandi</label>
            <div className="relative">
              <Lock className="absolute left-3 top-3 text-gray-400" size={18} />
              <input 
                type="password" 
                placeholder="••••••••"
                className="w-full pl-10 pr-4 py-3 border border-gray-200 rounded focus:border-[#00529B] outline-none"
              />
            </div>
          </div>

          <div className="flex items-center justify-between text-xs font-bold">
            <label className="flex items-center gap-2 text-gray-600 cursor-pointer">
              <input type="checkbox" className="rounded" /> INGAT SAYA
            </label>
            <a href="#" className="text-[#00529B] hover:underline">LUPA PASSWORD?</a>
          </div>

          <button className="w-full bg-[#00529B] text-white py-4 font-bold flex items-center justify-center gap-2 hover:bg-blue-800 transition-all rounded shadow-lg uppercase italic">
            Masuk Sekarang <ArrowRight size={18} />
          </button>

          <div className="relative py-4">
            <div className="absolute inset-0 flex items-center"><div className="w-full border-t border-gray-100"></div></div>
            <div className="relative flex justify-center text-xs uppercase"><span className="bg-white px-2 text-gray-400">Atau masuk dengan</span></div>
          </div>

          <div className="grid grid-cols-2 gap-4">
            <button className="border border-gray-200 py-3 rounded text-sm font-bold hover:bg-gray-50 transition-colors uppercase tracking-tighter">Google</button>
            <button className="border border-gray-200 py-3 rounded text-sm font-bold hover:bg-gray-50 transition-colors uppercase tracking-tighter">Apple ID</button>
          </div>
        </form>
      </div>
    </div>
  );
};

export default function App() {
  const [isAuthOpen, setIsAuthOpen] = useState(false);
  const [searchQuery, setSearchQuery] = useState('');

  // Fungsi untuk kembali ke Beranda (Reset Semua)
  const handleGoHome = () => {
    setSearchQuery('');
    window.scrollTo({ top: 0, behavior: 'smooth' });
  };

  // Logika Filter Produk
  const filteredProducts = useMemo(() => {
    return PRODUCTS.filter(product => 
      product.name.toLowerCase().includes(searchQuery.toLowerCase()) ||
      product.category.toLowerCase().includes(searchQuery.toLowerCase())
    );
  }, [searchQuery]);

  return (
    <div className="min-h-screen bg-[#F8F9FA] text-[#212529] font-sans">
      <Navbar 
        onOpenLogin={() => setIsAuthOpen(true)} 
        searchQuery={searchQuery}
        setSearchQuery={setSearchQuery}
        onGoHome={handleGoHome}
      />
      
      {/* Hero Section - Akan muncul kembali jika handleGoHome dipanggil */}
      {!searchQuery && (
        <section className="relative h-[70vh] bg-black overflow-hidden flex items-center">
          <div className="absolute inset-0 opacity-60">
            <img 
              src="https://images.unsplash.com/photo-1614200187524-dc4b892acf16?auto=format&fit=crop&q=80&w=2000" 
              alt="JDM Garage" 
              className="w-full h-full object-cover"
            />
          </div>
          <div className="relative max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 w-full">
            <div className="max-w-2xl">
              <h1 className="text-white text-5xl md:text-7xl font-black italic tracking-tighter mb-4 leading-none uppercase">
                TOTAL <span className="text-[#FFD700]">PERFORMANCE</span> <br />
                SINCE 1988
              </h1>
              <p className="text-gray-200 text-lg mb-8 max-w-md">
                Suku cadang balap premium yang dirancang khusus untuk kendaraan Honda. Presisi teknis bertemu estetika JDM.
              </p>
              <div className="flex gap-4">
                <a href="#products" className="bg-[#00529B] text-white px-8 py-4 font-bold rounded-sm flex items-center gap-2 hover:translate-x-1 transition-transform uppercase italic">
                  Belanja Sekarang <ChevronRight size={20} />
                </a>
                <button className="border-2 border-white text-white px-8 py-4 font-bold rounded-sm hover:bg-white/10 transition-colors uppercase italic">
                  Warisan Kami
                </button>
              </div>
            </div>
          </div>
        </section>
      )}

      <main className="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 py-16">
        
        {/* Breadcrumb / Back Navigation saat Filter aktif */}
        {searchQuery && (
          <div className="flex items-center gap-2 text-xs font-bold mb-6 text-gray-400 uppercase tracking-widest">
            <button onClick={handleGoHome} className="hover:text-[#00529B] flex items-center gap-1">
              <Home size={14} /> Beranda
            </button>
            <ChevronRight size={14} />
            <span className="text-[#00529B]">Hasil Pencarian</span>
          </div>
        )}

        {/* Compatibility Section */}
        {!searchQuery && <CompatibilityChecker />}

        {/* Categories Section */}
        {!searchQuery && (
          <div className="mb-16">
            <h2 className="text-3xl font-black italic mb-8 border-l-8 border-[#00529B] pl-4 uppercase">Belanja Berdasarkan Kategori</h2>
            <div className="grid grid-cols-2 md:grid-cols-4 gap-4">
              {['Engine', 'Drivetrain', 'Suspension', 'Wheels'].map(cat => (
                <div 
                  key={cat} 
                  onClick={() => {
                    setSearchQuery(cat);
                    window.scrollTo({ top: 0, behavior: 'smooth' });
                  }}
                  className="group relative h-40 bg-white border border-gray-200 rounded-lg overflow-hidden cursor-pointer hover:shadow-xl transition-all"
                >
                  <div className="absolute inset-0 bg-[#00529B]/5 group-hover:bg-[#00529B]/10 transition-colors"></div>
                  <div className="absolute bottom-4 left-4 font-black italic text-xl group-hover:text-[#00529B] uppercase">{cat}</div>
                  <ChevronRight className="absolute bottom-4 right-4 text-gray-300 group-hover:text-[#00529B]" size={24} />
                </div>
              ))}
            </div>
          </div>
        )}

        {/* Featured Products / Search Results */}
        <section id="products" className="mb-16 scroll-mt-20">
          <div className="flex flex-col md:flex-row justify-between items-start md:items-end mb-8 gap-4">
            <div>
              <h2 className="text-3xl font-black italic border-l-8 border-[#00529B] pl-4 uppercase">
                {searchQuery ? `Pencarian: "${searchQuery}"` : 'Suku Cadang Legendaris'}
              </h2>
              {searchQuery && (
                <p className="text-gray-400 text-sm mt-2 font-bold uppercase tracking-tighter">
                  Ditemukan {filteredProducts.length} produk
                </p>
              )}
            </div>
            {searchQuery && (
              <button 
                onClick={handleGoHome}
                className="bg-[#212529] text-white text-xs font-black px-4 py-2 rounded hover:bg-[#00529B] transition-colors uppercase italic"
              >
                Kembali ke Beranda
              </button>
            )}
          </div>
          
          {filteredProducts.length > 0 ? (
            <div className="grid grid-cols-1 md:grid-cols-3 gap-8">
              {filteredProducts.map(product => (
                <div key={product.id} className="bg-white group cursor-pointer border border-gray-100 rounded-lg overflow-hidden shadow-sm hover:shadow-md transition-shadow">
                  <div className="h-64 overflow-hidden relative">
                    <img 
                      src={product.image} 
                      alt={product.name} 
                      className="w-full h-full object-cover group-hover:scale-105 transition-transform duration-500"
                    />
                    <div className="absolute top-4 left-4 bg-[#FFD700] text-black text-[10px] font-black px-2 py-1 rounded">
                      TERSEDIA
                    </div>
                  </div>
                  <div className="p-6">
                    <div className="text-[10px] font-bold text-gray-400 mb-1 uppercase tracking-widest">{product.category}</div>
                    <h3 className="text-xl font-bold mb-2 group-hover:text-[#00529B] transition-colors uppercase italic">{product.name}</h3>
                    <p className="text-gray-500 text-sm mb-4 line-clamp-2">{product.description}</p>
                    <div className="flex justify-between items-center">
                      <span className="text-lg font-black text-[#212529] italic">{product.price}</span>
                      <button className="p-2 border border-gray-200 rounded hover:bg-[#00529B] hover:text-white transition-colors">
                        <ShoppingCart size={18} />
                      </button>
                    </div>
                  </div>
                </div>
              ))}
            </div>
          ) : (
            <div className="text-center py-20 bg-gray-50 rounded-xl border-2 border-dashed border-gray-200">
              <SearchX size={48} className="mx-auto text-gray-300 mb-4" />
              <h3 className="text-xl font-bold text-gray-500 uppercase italic">Produk Tidak Ditemukan</h3>
              <p className="text-gray-400 text-sm mt-2">Maaf, kami tidak dapat menemukan part yang cocok dengan "{searchQuery}".</p>
              <button 
                onClick={handleGoHome}
                className="mt-6 text-[#00529B] font-bold hover:underline uppercase text-sm"
              >
                Lihat Semua Produk
              </button>
            </div>
          )}
        </section>

        {/* Security / Info Banner */}
        <div className="bg-white border-y border-gray-200 py-12 px-8 rounded-lg flex flex-col md:flex-row items-center justify-between gap-8">
          <div className="flex gap-6 items-center">
            <div className="bg-[#F8F9FA] p-4 rounded-full border border-gray-200">
              <ShieldCheck size={48} className="text-[#00529B]" />
            </div>
            <div>
              <h4 className="font-bold text-lg mb-1 italic uppercase">Transaksi Aman</h4>
              <p className="text-gray-500 text-sm max-w-sm">
                Enkripsi TLS/SSL standar industri & integrasi gateway pembayaran yang aman (Midtrans/Xendit).
              </p>
            </div>
          </div>
          <div className="flex gap-4">
             <div className="text-center px-4">
                <div className="font-black text-2xl italic tracking-tighter text-[#00529B]">100%</div>
                <div className="text-[10px] text-gray-400 font-bold uppercase tracking-wider">Part Original</div>
             </div>
             <div className="w-px h-12 bg-gray-200"></div>
             <div className="text-center px-4">
                <div className="font-black text-2xl italic tracking-tighter text-[#00529B]">24H</div>
                <div className="text-[10px] text-gray-400 font-bold uppercase tracking-wider">Dukungan Teknis</div>
             </div>
          </div>
        </div>
      </main>

      {/* Footer */}
      <footer className="bg-[#212529] text-white py-16">
        <div className="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
          <div className="grid grid-cols-1 md:grid-cols-4 gap-12">
            <div className="col-span-1 md:col-span-2">
              <div onClick={handleGoHome} className="bg-[#00529B] text-white font-black px-4 py-2 italic tracking-tighter text-2xl w-fit mb-6 cursor-pointer">
                SPOON <span className="text-[#FFD700]">SPORTS</span>
              </div>
              <p className="text-gray-400 text-sm max-w-sm">
                Berdedikasi untuk memberikan performa maksimal tanpa kompromi. Dikembangkan di sirkuit, disempurnakan untuk jalan raya.
              </p>
            </div>
            <div>
              <h5 className="font-bold text-[#FFD700] mb-4 italic uppercase">Tautan Cepat</h5>
              <ul className="space-y-2 text-sm text-gray-300">
                <li><a href="#" className="hover:text-white">Kebijakan Pengiriman</a></li>
                <li><a href="#" className="hover:text-white">Lacak Pesanan</a></li>
                <li><a href="#" className="hover:text-white">Informasi Garansi</a></li>
                <li><a href="#" className="hover:text-white">Hubungi Kami</a></li>
              </ul>
            </div>
            <div>
              <h5 className="font-bold text-[#FFD700] mb-4 italic uppercase">Buletin</h5>
              <div className="flex">
                <input 
                  type="email" 
                  placeholder="Email Anda" 
                  className="bg-gray-800 border-none p-2 text-sm w-full rounded-l outline-none focus:ring-1 focus:ring-[#00529B]"
                />
                <button className="bg-[#00529B] px-4 py-2 rounded-r font-bold text-xs uppercase italic">Gabung</button>
              </div>
            </div>
          </div>
          <div className="border-t border-gray-800 mt-12 pt-8 text-center text-xs text-gray-500 uppercase tracking-widest">
            © 2024 SPOON PERFORMANCE. SELURUH HAK CIPTA DILINDUNGI. DIBUAT UNTUK ANTUSIAS.
          </div>
        </div>
      </footer>

      <AuthModal isOpen={isAuthOpen} onClose={() => setIsAuthOpen(false)} />
    </div>
  );
}

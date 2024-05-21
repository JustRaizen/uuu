products = {
  "beras": {"nama": "Beras", "harga": 45000, "satuan": "kardus", "stok": 4},
  "kopi": {"nama": "Kopi", "harga": 10000, "satuan": "sachet", "stok": 2},
  "kecap": {"nama": "Kecap", "harga": 12000, "satuan": "botol", "stok": 3},
}
def sell_product(nama_produk, jumlah):
  if nama_produk in products:
    produk = products[nama_produk]
    if jumlah <= 0:
      print("Jumlah tidak valid. Masukkan bilangan positif.")
      return
    if jumlah > produk["stok"]:
      print(f"Stok {produk['nama']} tidak mencukupi. Hanya {produk['stok']} {produk['satuan']} tersedia.")
      return
    
    # Logika Diskon (modifikasi sesuai aturan diskon Anda)
    diskon = 0
    # Contoh diskon untuk pembelian 2 atau lebih unit produk yang sama
    if jumlah >= 2:
      diskon = 0.05  # Diskon 5%

    # Hitung total harga dengan diskon
    total_harga = produk["harga"] * jumlah * (1 - diskon)
    
    # Perbarui stok
    produk["stok"] -= jumlah
    
    # Cetak struk
    print(f"--- Struk ---")
    print(f"Produk: {produk['nama']}")
    print(f"Jumlah: {jumlah} {produk['satuan']}")
    print(f"Harga Satuan: Rp{produk['harga']:,.2f}")
    print(f"Diskon: Rp{diskon * total_harga:,.2f} ({diskon * 100:.0f}%)")
    print(f"Total Harga: Rp{total_harga:,.2f}")
    print("-" * 20)
  else:
    print(f"Produk '{nama_produk}' tidak ditemukan.")
sell_product("beras", 2)  # Beli 2 kardus beras
sell_product("kopi", 1)  # Beli 1 sachet kopi
sell_product("kecap", 2)  # Beli 2 botol kecap
sell_product("unknown", 1)  # Cek produk tidak ada

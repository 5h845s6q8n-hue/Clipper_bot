
import instaloader

# Daftar akun target yang sudah kamu pilih
target_accounts = ["apexmetalrestoration", "kaadanlife", "technicalcrafter"]

def harvest_bol():
    L = instaloader.Instaloader()
    print("--- Memulai Pemindaian Konten ---")
    
    for username in target_accounts:
        try:
            print(f"Memeriksa akun: {username}")
            profile = instaloader.Profile.from_username(L.context, username)
            
            # Mengambil 1 postingan terbaru sebagai sampel
            for post in profile.get_posts():
                print(f"Konten Baru Ditemukan! ID: {post.shortcode}")
                print(f"Link Video: {post.url}")
                break # Hanya ambil 1 yang paling baru
                
        except Exception as e:
            print(f"Gagal memproses {username}: {e}")

if __name__ == "__main__":
    harvest_bol()

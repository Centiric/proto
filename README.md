# Centiric Platform - API Tanımları

Bu repository, Centiric mikroservis platformunun tüm gRPC API tanımlarını (.proto dosyaları) barındırır. Bu, servisler arası iletişimin "tek gerçek kaynağıdır" (single source of truth).

## Kullanım

Bu repo, diğer servisler tarafından bir **Git Submodule** olarak kullanılmak üzere tasarlanmıştır.

### Bir Servise Submodule Olarak Ekleme

Örneğin, `core` servisine eklemek için:
```bash
cd /path/to/core
git submodule add https://github.com/Centiric/proto.git third_party/proto
```

### Kod Üretme

Her servis, kendi `protoc` veya `tonic-build` komutunu çalıştırarak bu tanımlardan kendi diline uygun kodları üretmelidir.

**Örnek `protoc` komutu (Go için):**
```bash
protoc --go_out=. --go-grpc_out=. \
       -I ./third_party/proto \
       ./third_party/proto/core/v1/core.proto
```

## Versiyonlama

Tüm API'ler `v1`, `v2` gibi klasörler altında versiyonlanmalıdır. Geriye dönük uyumluluğu bozan değişiklikler yeni bir versiyon gerektirir.


---

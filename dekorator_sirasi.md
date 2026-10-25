#GÖREV 2-Cagri Sayaci ve Dekorator Sırası Acıklaması

Ozyinelemeli Fibonacci('fib(20)') fonksiyonu uzerinde 'say' ve 'lru cache' dekoratorlerinin uygulanıs sırası cagri sayısını ve calısma mantıgını dogrudan etkiler:
1. **Yalnızca @say (21891):**
-Onbellekleme olmadıgı icin her özyineleme adımı alt dallara (fib(n-1) ve fib(n-2) ayrılarak aynı degerleri tekrar tekrar hesaplar. Toplam cagrı sayısı ussel olarak artar.)
2. **@say üstte, @lru_cache altta (39 cagrı):**
- Dısardaki '@say' her cagrıyı sayar. İcteki 'lru_cache' önbellek vurusları (cache hit) sagladıgı icin alt dallardaki tekrarlı hesaplamalar önbellekten döner. Bu sayede ana fonksiyon cok daha az kez tetiklenir(39 cagri).
3. **@lru_cache üstte, @say altta (21 cagrı):**
-Dısarıda 'lru_cache', icte '@say' bulunur.'fib(20)' cagrıldıgında önce 'lru_cache' devreye girer. Sonuc önbellekte varsa dogryudan doner ve icteki '@say' hic calismaz. Sadece önbellek iskalamalarında (cache miss) icteki '@say' calisarak hesaplama yapar. İcteki sayaca bu durumda 'fib__wrapped__.cagri' uzerinden erilesilebilir.
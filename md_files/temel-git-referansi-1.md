# Temel Git Referansı - 1

## Git Yardım Sayfaları
- Genel yardım:
```
git help
```
- Özel bir git fonksiyonalitesi hakkında yardım (örneğin commit komutu)
```
git help commit
```

## Başlangıç Konfigürasyonları
- Kullanıcı adı, email konfigürasyonu
```
git config --global user.name <kullanıcı adı>
git config --global user.email <mail adresi>
```

- Tercihen yapılabilecek default branch konfigürasyonu ve editör konfigürasyonu
```
git config --global init.defaultBranch <branch ismi>
git config --global core.editor <editör>
```

## Repository Oluşturma
- Komut satırında ilgili proje klasörü içindeyken uygulanır, ".git" klasörünü oluşturur. 
```
git init
```

## Mevcut Bir Repo'yu Çekme
```
git clone <url> <klasör ismi (opsiyonel)>
```

## Commit'e Dosya Hazırlama (Dosyayı Staged Konumuna Getirme)
- Dosya ismi yerine "." ifadesi verilerek klasördeki tüm dosyalar da staged edilebilir.
```
git add <dosya ismi>
```

## Untracked, Unmodified, Modified ve Staged Durumları
- Daha önce "git add" komutu ile eklenmemiş dosyalar untracked durumdadır.
- Son commit sonrasında değişikliğe uğramamış ve daha önce "git add" ile eklenmiş de olan dosyalar unmodified sınıfındadır.
- Modified olanlar ise değişime uğradıktan sonra "git add" ile staged edilmemiş dosyalardır.
- Staged olanlar ise "git add" ile eklenmiş ancak henüz commit edilmemiş durumda olanlardır.

## Mevcut Durumu Görüntüleyen Komutlar
- Uzun ve kısa çıktı veren iki ayrı dosyaların durumunu göstermeye yardımcı komut:
```
git status
git status -s
```

## Commit Etme
- Burada "-m" parametresi commit mesajının girilmesini sağlar, "-m" kullanılmaz ise varsayılan editör bu commit mesajının girilmesi için açılır.
```
git commit -m <commit mesajı>
```

## Belli Dosyaları Yok Sayma
- ".gitignore" isimli bir metin dosyasına ilgili dosya isim ve yolları girilerek, yanlışlıkla istenmeyen dosyaların (örneğin IDE'lere özel projeyle doğrudan bağlantılı olmayan dosyalar gibi) takibinin yapılmasının önüne geçilebilir.
- https://github.com/github/gitignore sayfasında örnekler mevcuttur.

## Dosyalar Üzerinde Oluşmuş Değişiklikleri Görmek
- Sırasıyla aşağıdaki komutlarla değişmiş olup staged olmayan ve staged olan dosyalardaki değişimler görülüyor.
```
git diff
git diff --staged
```

## Git ile Dosya Silme
- Dosyayı hem sistemden hem de Git'in takibinden kaldırmak için:
```
git rm <dosya ismi>
```
- Modified veya Staged durumda olanların silinmesi:
```
git rm -f <dosya ismi>
```
- Aşağıdaki komut ise dosyayı sistemde korurken Git'in dosyayı takibini kaldırır:
```
git rm --cached <dosya ismi>
```

## Git Logları
- Commit'lerin checksum, author, date ve message bilgilerinin ters kronolojik sırada gösterimi:
```
git log
```
- Örnek olarak son 2 commit ve yapılan değişiklikleri görmek istersek aşağıdaki komut yardımcı olacaktır:
```
git log -p -2
```
- Kısaltılmış şekilde hangi dosyaların ne yönde değiştiğinin gösterimi:
```
git log --stat
```
- Her bir commit'in tek satırda checksum ve mesaj bilgilerinin gösterimi:
```
git log --pretty=oneline
```
- Branch ve merge bilgilerinin graph formatında gösterimi:
```
git log --graph
```
- Sadece belirli dosyaya yönelik commit'lerin listelenişi:
```
git log -- <dosya yolu>
```
- Log gösterimlerinde "--no-merges" ile merge commit'leri gizlenebilir.
- "--since", "--until", "--grep" ve "--author" gibi çıktı limitleme parametreleri de kullanılabilmektedir.

## Değişiklikleri Geri Alma
- Commit sonrası yapılacak bir değişiklik daha olduğu hatırlandığında son commit'e ekleme yapma yönünde bir örnek:
```
git commit -m "ilk commit"
git add unutulmus_dosya
git commit --amend -m "<commit mesajı>"
```
- Bir dosyayı unstage etmek için aşağıdaki komutlardan herhangi biri kullanılabilir:
```
git reset HEAD <dosya ismi>
git restore --staged <dosya ismi>
```
- Dosyayı unmodify etmek için ise aşağıdaki komutlardan herhangi biri kullanılabilir:
- Bu komutlardan birinin kullanımı sonrası dosyanın eski haline geri döndürülemeyebileceği unutulmamalı.
```
git checkout -- <dosya ismi>
git restore <dosya ismi>
```

## Remote Repository'lerle Çalışmak
- Mevcutta bir remote repo ile çalışılınmaktaysa remote'un veya remote'ların kısa adı ve URL'i aşağıdaki komutla görülebilir:
```
git remote -v
```
- Bir remote repo'yu indirmek için:
```
git clone <repo url>
```
- Remote ekleme:
```
git remote add <remote için kısa isim> <remote repo url>
```
- Fetch ile remote repo'yu çekmek (kodunuzu güncellemek isterseniz devamında manuel olarak merge işlemi gerektirir):
```
git fetch <remote'a verilmiş kısa isim>
```
- Pull işlemi (fetch ile benzer şekildedir ancak manuel merge gerektirmez)
- Local'deki branch ile remote branch aynı ise pull sonrası kodunuz remote'takine güncellenir
```
git pull <remote'a verilmiş kısa isim> <branch ismi>
```
- Remote Repo'ya Pushlamak:
- Not: Başkasının push'ladığının üstüne push'lama geçtiğiniz de reject alırsınız.
```
git push <remote kısa ismi> <branch ismi>
```
- Remote hakkında bilgi edinmek:
```
git remote show <remote kısa ismi>
```
- Remote'u yeniden adlandırma komutu ve silmek için komutlar:
```
git remote rename <mevcut remote kısa ismi> <mevcut remote'un yeni kısa ismi>
git remote rm <remote kısa ismi>
git remote remove <remote kısa ismi>
```

## Tag Ekleme İşlemleri
- Annotated tag'ler ve lightweight tag'ler bulunmaktadır, annotated olanlar tag'lendiği kısım ile ilgili daha fazla bilgi tutar.
- Sırasıyla annotated ve lightweight tag ekleme örnekleri:
```
git tag -a v1.4 -m "versiyonum 1.4"
git show v1.4

git tag v1.4-lw
git show v1.4-lw
```
- Daha sonrasında commit'e tag ekleme:
```
git tag -a <tag ismi> <commit checksum>
```
- Tag'ler otomatik push'lanmadığı için elle pushlamak gerekmektedir.
- Tüm tag'leri push'lama örneği:
```
git push <remote kısa isim> --tags
```
- Belli bir tag'i pushlama:
```
git push <remote kısa isim> <tag ismi>
```
- Sırasıyla tag silme ve remote'tan tag silme örnekleri:
```
git tag -d <tag ismi>
git push <remote kısa isim> --delete <tag ismi>
```

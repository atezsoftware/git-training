# git branching

## main

her seyin basi ve sonu bu branch olmali.

Tum gelistirmeler icin buradan branch almalisiniz, branchiniz tum asamalari
gecip buraya merge edildigine feature branchinizla isiniz bitmistir demektir,
artik silebilirsiniz.

## release/v1

release takvimine bagli olarak main branch'i buraya merge edip, gelistirmeleri
canliya cikacaginiz branch. main'e atilan her sey takvimi geldiginde release
edilecektir. db migration gibi konulari da dusunurek bunu kontrollu
gerceklestirmek isteriz.

canlidaki bir bug'i fix etmek istedigimizde (hotfix), main'den degil,
release'den branch almak isteriz. Boylece main'deki henuz canliya atilmamis
gelistirmeleri canliya atmak zorunda kalmadan problemi cozup release'e merge
ederek deploy cikabiliriz.

## develop(ment)

gelistirme ortamina deploy edilen branch. gelistirme yaptigimiz tum branch'lerin
ilk duragi burasidir, local'deki calismalar bir noktaya ulastiginda
gelistirmeleri deploy edip cloud'da calistirabiliriz, frontend backend tarafinda
calisma gerektigi durumda calismalara bu ortamdan devam ederiz, gelistirmeler
tamamlaninca test branchine tasiriz.

## test/v1

test ortamina deploy edilen branchimiz. develop ortaminda gelistirmeler
tamamlaninca ve kabul testleri icin bu ortama merge edip business ekibi
tarafindan kabul testlerinin yapilmasini bu ortamda saglariz. Burada bug cikarsa
ayni feature branch'i uzerinden gelistirmelere devam ederiz.

## branching

### naming

genel olarak main'den aldiginiz tum branch'leri

feat(ure)/ticket-code_tanim-icin-birkac-kelime

release'den branch aldiginizde feature yerine hotfix kullanmaliyiz.

Yapacaginiz gelistirmelerin %90'i bu feature branch'ler uzerinde olacaktir, ek
olarak bug'lar icin fix prefixini kullanabilirsiniz.

fix/ticket-code-fix-something

bunlar disinda docs, ref, chore gibi prefixler'de uygun senaryolarda
kullanilabilir.

### multi branch

epic veya birden fazla development gereken story'ler de ana epic/story id'si ile
bir branch acip, bu branch'ten feature branch'leri olusturabilirsiniz, en son
her sey ilk once bu branch'te merge olur, sonrasinda main'e gider.

```bash
feat/epic-story-no
  |
  |-- feat/sub-story-1
  |-- feat/sub-story-2
```

## pull request

tum merge'ler pull request (PR) ile yapilir, PR acmadan once 'rebase' etmeniz
gerekir, normal calisma akisinda, uzun sureli development'larda, her gun
main'den tekrar rebase etmenizi onerilir.

PR'lari onayladiginizda ise, squash and merge secenegi ile merge etmeniz bu
degisikligin geri alinmasi gibi senaryolarda yardimci olacaktir.

## resetting

develop ve test branch'lari deployment branch'laridir, bu branch'lari
istediginiz zaman main'den resetleyebiliyor olmalisiniz. Her sprint sonunda bu
islemi yapmanizi oneririz, calisma devam eden branch'leri tekrar birlestirmek
gerekecektir.

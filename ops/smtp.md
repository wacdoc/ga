Cuir isteach an stóras cumraíochta ops.soft, rith `./ssl.sh` , agus cruthófar fillteán `conf` san **eolaire uachtarach** .

## brollach

Is féidir le SMTP seirbhísí a cheannach go díreach ó dhíoltóirí néil, mar:

* [Amazon SES SMTP](https://docs.aws.amazon.com/ses/latest/dg/send-email-smtp.html)
* [Brúigh ríomhphoist scamall Ali](https://www.alibabacloud.com/help/directmail/latest/three-mail-sending-methods)

Is féidir leat do fhreastalaí ríomhphoist féin a thógáil freisin - seoladh neamhtheoranta, costas iomlán íseal.

Anseo thíos, léirímid céim ar chéim conas ár bhfreastalaí ríomhphoist féin a thógáil.

## Roghnú freastalaí

Éilíonn an freastalaí SMTP féin-óstach IP poiblí le calafoirt 25, 456, agus 587 oscailte.

Chuir scamaill phoiblí a úsáidtear go coitianta bac ar na calafoirt seo de réir réamhshocraithe, agus b'fhéidir go bhféadfaí iad a oscailt trí ordú oibre a eisiúint, ach tá sé an-trioblóideach tar éis an tsaoil.

Molaim ceannach ó óstach a bhfuil na calafoirt seo oscailte aige agus a thacaíonn le hainmneacha fearainn droim ar ais a bhunú.

Anseo, molaim [Contabo](https://contabo.com) .

Is soláthraí óstála é Contabo atá lonnaithe i München, an Ghearmáin, a bunaíodh i 2003 le praghsanna an-iomaíoch.

Má roghnaíonn tú Euro mar airgeadra ceannaigh, beidh an praghas níos saoire (cosnaíonn freastalaí le cuimhne 8GB agus 4 CPUs thart ar 529 yuan in aghaidh na bliana, agus tá an táille suiteála tosaigh saor in aisce ar feadh bliana).

![](https://pub-b8db533c86124200a9d799bf3ba88099.r2.dev/2023/03/UoAQkwY.webp)

Agus ordú á dhéanamh, `prefer AMD` , agus beidh feidhmíocht níos fearr ag an bhfreastalaí le AMD CPU.

San méid seo a leanas, tógfaidh mé VPS Contabo mar shampla chun a léiriú conas do fhreastalaí ríomhphoist féin a thógáil.

## Cumraíocht chórais Ubuntu

Is é an córas oibriúcháin anseo ná Ubuntu 22.04

![](https://pub-b8db533c86124200a9d799bf3ba88099.r2.dev/2023/03/smpIu1F.webp)

![](https://pub-b8db533c86124200a9d799bf3ba88099.r2.dev/2023/03/m7Mwjwr.webp)

Má thaispeánann an freastalaí ar ssh `Welcome to TinyCore 13!` (mar a thaispeántar san fhigiúr thíos), ciallaíonn sé nach bhfuil an córas suiteáilte fós. Déan ssh a dhícheangal le do thoil agus fan ar feadh cúpla nóiméad chun logáil isteach arís.

![](https://pub-b8db533c86124200a9d799bf3ba88099.r2.dev/2023/03/-qKACz9.webp)

Nuair a fheictear `Welcome to Ubuntu 22.04.1 LTS` , tá an t-inisealú críochnaithe, agus is féidir leat leanúint ar aghaidh leis na céimeanna seo a leanas.

### [Roghnach] Cuir tús leis an timpeallacht forbartha

Tá an chéim seo roghnach.

Ar mhaithe le caoithiúlacht, chuir mé suiteáil agus cumraíocht chórais bogearraí ubuntu i [github.com/wactax/ops.os/tree/main/ubuntu](https://github.com/wactax/ops.os/tree/main/ubuntu) .

Rith an t-ordú seo a leanas a shuiteáil le cliceáil amháin.

```
bash <(curl -s https://raw.githubusercontent.com/wactax/ops.os/main/ubuntu/boot.sh)
```

Úsáideoirí na Síne, bain úsáid as an ordú seo a leanas ina ionad sin, agus socrófar an teanga, an crios ama, etc. go huathoibríoch.

```
CN=1 bash <(curl -s https://ghproxy.com/https://raw.githubusercontent.com/wactax/ops.os/main/ubuntu/boot.sh)
```

### Cumasaíonn Contabo IPV6

Cumasaigh IPV6 ionas gur féidir le SMTP ríomhphoist le seoltaí IPV6 a sheoladh freisin.

in eagar `/etc/sysctl.conf`

Athraigh nó cuir na línte seo a leanas leis

```
net.ipv6.conf.all.disable_ipv6 = 0
net.ipv6.conf.default.disable_ipv6 = 0
net.ipv6.conf.lo.disable_ipv6 = 0
```

Lean ar aghaidh leis [an teagaisc contabo: Nascacht IPv6 a chur le do fhreastalaí](https://contabo.com/blog/adding-ipv6-connectivity-to-your-server/)

Cuir `/etc/netplan/01-netcfg.yaml` , cuir cúpla líne leis mar a thaispeántar san fhigiúr thíos (tá na línte seo ag an gcomhad cumraíochta réamhshocraithe Contabo VPS cheana féin, gan trácht orthu).

![](https://pub-b8db533c86124200a9d799bf3ba88099.r2.dev/2023/03/5MEi41I.webp)

Ansin `netplan apply` chun an chumraíocht leasaithe a chur i bhfeidhm.

Tar éis don chumraíocht a bheith rathúil, is féidir leat `curl 6.ipw.cn` a úsáid chun seoladh ipv6 do líonra seachtrach a fheiceáil.

## Clón comharchumainn an taisc chumraíochta

```
git clone https://github.com/wactax/ops.soft.git
```

## Gin teastas SSL saor in aisce do d’ainm fearainn

Teastaíonn teastas SSL le haghaidh criptiúcháin agus sínithe chun ríomhphost a sheoladh.

Bainimid úsáid as [acme.sh](https://github.com/acmesh-official/acme.sh) chun teastais a ghiniúint.

Is uirlis sínithe deimhnithe uathoibrithe foinse oscailte é acme.sh,

Cuir isteach an stóras cumraíochta ops.soft, rith `./ssl.sh` , agus cruthófar fillteán `conf` san **eolaire uachtarach** .

Aimsigh do sholáthraí DNS ó [acme.sh dnsapi](https://github.com/acmesh-official/acme.sh/wiki/dnsapi) , cuir in eagar `conf/conf.sh` .

![](https://pub-b8db533c86124200a9d799bf3ba88099.r2.dev/2023/03/Qjq1C1i.webp)

Ansin rith `./ssl.sh 123.com` chun teastais `123.com` agus `*.123.com` a ghiniúint do d'ainm fearainn.

Déanfaidh an chéad rith [acme.sh](https://github.com/acmesh-official/acme.sh) a shuiteáil go huathoibríoch agus cuirfidh sé tasc sceidealaithe le haghaidh athnuachan uathoibríoch. Is féidir leat `crontab -l` a fheiceáil , tá a leithéid de líne mar seo a leanas.

```
52 0 * * * "/mnt/www/.acme.sh"/acme.sh --cron --home "/mnt/www/.acme.sh" > /dev/null
```

Is é cosán an deimhnithe ginte rud éigin cosúil le `/mnt/www/.acme.sh/123.com_ecc。`

Glaofaidh athnuachan teastais ar `conf/reload/123.com.sh` script, cuir an script seo in eagar, is féidir leat orduithe a chur leis mar `nginx -s reload` chun taisce teastais na n-iarratas gaolmhar a athnuachan.

## Tóg freastalaí SMTP le chasquid

Is freastalaí SMTP foinse oscailte é [chasquid](https://github.com/albertito/chasquid) atá scríofa i dteanga Go.

Mar ionadach ar na cláir freastalaí ríomhphoist ársa mar Postfix agus Sendmail, tá chasquid níos simplí agus níos éasca le húsáid, agus tá sé níos éasca freisin d'fhorbairt thánaisteach.

Run `./chasquid/init.sh 123.com` a shuiteáil go huathoibríoch le cliceáil amháin (cuir d'ainm fearainn seolta in ionad 123.com).

## Cumraigh Síniú Ríomhphoist DKIM

Úsáidtear DKIM chun sínithe ríomhphoist a sheoladh chun cosc ​​a chur ar litreacha a láimhseáil mar thurscar.

Tar éis don ordú rith go rathúil, tabharfar leid duit an taifead DKIM a shocrú (mar a thaispeántar thíos).

![](https://pub-b8db533c86124200a9d799bf3ba88099.r2.dev/2023/03/LJWGsmI.webp)

Just a cuir taifead TXT le do DNS (mar a thaispeántar thíos).

![](https://pub-b8db533c86124200a9d799bf3ba88099.r2.dev/2023/03/0szKWqV.webp)

## Féach ar stádas seirbhíse & logaí

 `systemctl status chasquid` Féach ar stádas seirbhíse.

Tá staid na gnáthoibríochta mar a thaispeántar san fhigiúr thíos

![](https://pub-b8db533c86124200a9d799bf3ba88099.r2.dev/2023/03/CAwyY4E.webp)

 `grep chasquid /var/log/syslog` nó `journalctl -xeu chasquid` is féidir leis an loga earráide a fheiceáil.

## Cumraíocht ainm fearainn droim ar ais

Tá an t-ainm fearainn droim ar ais chun an seoladh IP a réiteach don ainm fearainn comhfhreagrach.

Má shocraítear ainm fearainn droim ar ais ní féidir teachtaireachtaí ríomhphoist a aithint mar thurscar.

Nuair a fhaightear an ríomhphost, déanfaidh an freastalaí glactha anailís ainm fearainn droim ar ais ar sheoladh IP an fhreastalaí seolta chun a dhearbhú an bhfuil ainm fearainn droim ar ais bailí ag an bhfreastalaí seolta.

Mura bhfuil ainm fearainn droim ar ais ag an bhfreastalaí seolta nó mura bhfuil an t-ainm fearainn droim ar ais ag teacht le seoladh IP an fhreastalaí seolta, féadfaidh an freastalaí glactha an ríomhphost a aithint mar thurscar nó é a dhiúltú.

Tabhair cuairt ar [https://my.contabo.com/rdns](https://my.contabo.com/rdns) agus cumraigh mar a thaispeántar thíos

![](https://pub-b8db533c86124200a9d799bf3ba88099.r2.dev/2023/03/IIPdBk_.webp)

Tar éis duit an t-ainm fearainn droim ar ais a shocrú, cuimhnigh ar réiteach ar aghaidh an ainm fearainn ipv4 agus ipv6 a chumrú don fhreastalaí.

## Cuir an t-óstainm ar chasquid.conf in eagar

Athraigh `conf/chasquid/chasquid.conf` go luach an ainm fearainn droim ar ais.

![](https://pub-b8db533c86124200a9d799bf3ba88099.r2.dev/2023/03/6Fw4SQi.webp)

Ansin rith `systemctl restart chasquid` chun an tseirbhís a atosú.

## Cúltaca conf le stór git

![](https://pub-b8db533c86124200a9d799bf3ba88099.r2.dev/2023/03/Fier9uv.webp)

Mar shampla, déanaim an fillteán conf a chúltaca le mo phróiseas github féin mar seo a leanas

Cruthaigh stóras príobháideach ar dtús

![](https://pub-b8db533c86124200a9d799bf3ba88099.r2.dev/2023/03/ZSCT1t1.webp)

Cuir isteach an t-eolaire conf agus cuir isteach chuig an stóras

```
git init
git add .
git commit -m "init"
git branch -M main
git remote add origin git@github.com:wac-tax-key/conf.git
git push -u origin main
```

## Cuir seoltóir leis

rith

```
chasquid-util user-add i@wac.tax
```

Is féidir seoltóir a chur leis

![](https://pub-b8db533c86124200a9d799bf3ba88099.r2.dev/2023/03/khHjLof.webp)

### Deimhnigh go bhfuil an pasfhocal socraithe i gceart

```
chasquid-util authenticate i@wac.tax --password=xxxxxxx
```

![](https://pub-b8db533c86124200a9d799bf3ba88099.r2.dev/2023/03/e92JHXq.webp)

Tar éis an t-úsáideoir a chur leis, déanfar `chasquid/domains/wac.tax/users` a nuashonrú, cuimhnigh é a chur isteach sa stóras.

## Cuireann DNS taifead SPF leis

Is teicneolaíocht fíoraithe ríomhphoist é SPF ( Creat Beartais Seoltóra ) a úsáidtear chun calaois ríomhphoist a chosc.

Fíoraíonn sé céannacht seoltóir ríomhphoist trína sheiceáil go bhfuil seoladh IP an tseoltóra ag teacht le taifid DNS an ainm fearainn a mhaíonn sé a bheith, rud a chuireann cosc ​​ar chaimiléirí ríomhphoist bhréagacha a sheoladh.

Má chuirtear taifid SPF leis is féidir cosc ​​a chur ar ríomhphoist a aithint mar thurscar a oiread agus is féidir.

Mura dtacaíonn do fhreastalaí ainm fearainn le cineál SPF, ní gá ach taifead cineál TXT a chur leis.

Mar shampla, is é seo a leanas an SPF de `wac.tax`

`v=spf1 a mx include:_spf.wac.tax include:_spf.google.com ~all`

SPF le haghaidh `_spf.wac.tax`

`v=spf1 a:smtp.wac.tax ~all`

Tabhair faoi deara go bhfuil `include:_spf.google.com` anseo, tá sé seo toisc go ndéanfaidh mé `i@wac.tax` a chumrú mar an seoladh seolta i mbosca ríomhphoist Google níos déanaí.

## Cumraíocht DNS DMARC

Is é DMARC an giorrúchán de (Fíordheimhniú Teachtaireachtaí Fearainn-bhunaithe, Tuairisciú & Comhlíonadh).

Úsáidtear é chun preabanna SPF a ghabháil (b’fhéidir gur earráidí cumraíochta ba chúis leis, nó go bhfuil duine éigin eile ag ligean air féin gur tusa atá ann chun turscar a sheoladh).

Cuir taifead TXT `_dmarc` ,

Seo a leanas an t-ábhar

```
v=DMARC1; p=quarantine; fo=1; ruf=mailto:ruf@wac.tax; rua=mailto:rua@wac.tax
```

![](https://pub-b8db533c86124200a9d799bf3ba88099.r2.dev/2023/03/k44P7O3.webp)

Is é seo a leanas brí gach paraiméadar

### p (Polasaí)

Léiríonn sé conas ríomhphoist a láimhseáil a dteipeann orthu fíorú SPF (Creat Beartais Seoltóra) nó DKIM (DomainKeys Aitheanta Mail). Is féidir an paraiméadar p a shocrú go ceann amháin de thrí luach:

* none: Ní dhéantar aon ghníomh, ní chuirtear ar ais don seoltóir ach an toradh fíoraithe tríd an meicníocht tuairiscithe ríomhphoist.
* Coraintín: Cuir an ríomhphost nár éirigh leis an bhfíorú isteach san fhillteán turscair, ach ní dhiúltóidh sé don phost go díreach.
* diúltaigh: Diúltaigh go díreach ríomhphoist a dteipeann fíorú.

### fo (Roghanna Teip)

Sonraítear an méid faisnéise a sheol an sásra tuairiscithe ar ais. Is féidir é a shocrú go ceann de na luachanna seo a leanas:

* 0: Tuairiscigh torthaí bailíochtaithe do gach teachtaireacht
* 1: Ná tuairiscigh ach teachtaireachtaí a theipeann ar an bhfíorú
* d: Ná tabhair tuairisc ach ar theipeanna fíoraithe ainm fearainn
* s: ná tuairiscigh ach teipeanna fíoraithe SPF
* l: Ná déan ach teipeanna fíoraithe DKIM a thuairisciú

### rua & ruf

* rua (URI Tuairiscithe le haghaidh tuarascálacha Comhiomlána): Seoladh ríomhphoist chun tuarascálacha comhiomlánaithe a fháil
* ruf (URI Tuairiscithe le haghaidh tuarascálacha Fóiréinseacha): seoladh ríomhphoist chun tuarascálacha mionsonraithe a fháil

## Cuir taifid MX leis chun ríomhphoist a chur ar aghaidh chuig Google Mail

Toisc nach raibh mé in ann bosca poist corparáideach saor in aisce a aimsiú a thacaíonn le seoltaí uilíocha (Catch-All, in ann aon ríomhphoist a seoladh chuig an ainm fearainn seo a fháil, gan srianta ar réimíreanna), d'úsáid mé chasquid chun gach ríomhphost a chur ar aghaidh chuig mo bhosca ríomhphoist Gmail.

**Má tá do bhosca poist gnó íoctha agat féin, ná modhnaigh an MX le do thoil agus ná fág an chéim seo.**

Cuir `conf/chasquid/domains/wac.tax/aliases` eagar , socraigh an bosca poist seolta ar aghaidh

![](https://pub-b8db533c86124200a9d799bf3ba88099.r2.dev/2023/03/OBDl2gw.webp)

Léiríonn `*` gach ríomhphost, `i` é i réimír seoladh ríomhphoist an úsáideora seolta a cruthaíodh thuas. Chun ríomhphost a chur ar aghaidh, ní mór do gach úsáideoir líne a chur leis.

Ansin cuir an taifead MX leis (cuirim in iúl go díreach seoladh an ainm fearainn droim ar ais anseo, mar a thaispeántar sa chéad líne san fhigiúr thíos).

![](https://pub-b8db533c86124200a9d799bf3ba88099.r2.dev/2023/03/7__KrU8.webp)

Tar éis don chumraíocht a bheith críochnaithe, is féidir leat seoltaí ríomhphoist eile a úsáid chun ríomhphoist a sheoladh chuig `i@wac.tax` agus `any123@wac.tax` féachaint an féidir leat ríomhphoist a fháil in Gmail.

Mura bhfuil, seiceáil an logáil chasquid ( `grep chasquid /var/log/syslog` ).

## Seol ríomhphost chuig i@wac.tax le Google Mail

Tar éis do Google Mail an ríomhphost a fháil, bhí súil agam go nádúrtha freagra a thabhairt le `i@wac.tax` in ionad i.wac.tax@gmail.com.

Tabhair cuairt ar [https://mail.google.com/mail/u/1/#settings/accounts](https://mail.google.com/mail/u/1/#settings/accounts) agus cliceáil "Cuir seoladh ríomhphoist eile leis".

![](https://pub-b8db533c86124200a9d799bf3ba88099.r2.dev/2023/03/PAvyE3C.webp)

![](https://pub-b8db533c86124200a9d799bf3ba88099.r2.dev/2023/03/_OgLsPT.webp)

![](https://pub-b8db533c86124200a9d799bf3ba88099.r2.dev/2023/03/XIUf6Dc.webp)

Ansin, cuir isteach an cód fíoraithe a fuair an ríomhphost a cuireadh ar aghaidh chuige.

Ar deireadh, is féidir é a shocrú mar an seoladh réamhshocraithe seoltóra (mar aon leis an rogha freagra a thabhairt leis an seoladh céanna).

![](https://pub-b8db533c86124200a9d799bf3ba88099.r2.dev/2023/03/a95dO60.webp)

Ar an mbealach seo, tá bunú an fhreastalaí ríomhphoist SMTP curtha i gcrích againn agus ag an am céanna úsáidimid Google Mail chun ríomhphoist a sheoladh agus a fháil.

## Seol ríomhphost tástála le seiceáil an bhfuil an chumraíocht rathúil

Cuir isteach `ops/chasquid`

Rith `direnv allow` spleáchais a shuiteáil (tá direnv suiteáilte sa phróiseas tosaigh aon-eochair roimhe seo agus tá duán curtha leis an mblaosc)

ansin rith

```
user=i@wac.tax pass=xxxx to=iuser.link@gmail.com ./sendmail.coffee
```

Is é seo a leanas brí na bparaiméadar

* úsáideoir: ainm úsáideora SMTP
* pas: pasfhocal SMTP
* chuig: faighteoir

Is féidir leat ríomhphost tástála a sheoladh.

![](https://pub-b8db533c86124200a9d799bf3ba88099.r2.dev/2023/03/ae1iWyM.webp)

Moltar Gmail a úsáid chun ríomhphoist tástála a fháil le seiceáil an bhfuil rath ar na cumraíochtaí.

### Criptiú caighdeánach TLS

Mar a thaispeántar san fhigiúr thíos, tá an glas beag seo ann, rud a chiallaíonn go bhfuil an teastas SSL cumasaithe go rathúil.

![](https://pub-b8db533c86124200a9d799bf3ba88099.r2.dev/2023/03/SrdbAwh.webp)

Ansin cliceáil "Taispeáin Ríomhphost Bunaidh"

![](https://pub-b8db533c86124200a9d799bf3ba88099.r2.dev/2023/03/qQQsdxg.webp)

### DKIM

Mar a thaispeántar san fhigiúr thíos, taispeánann leathanach ríomhphoist bunaidh Gmail DKIM, rud a chiallaíonn go n-éiríonn le cumraíocht DKIM.

![](https://pub-b8db533c86124200a9d799bf3ba88099.r2.dev/2023/03/an6aXK6.webp)

Seiceáil an Faighte i gceannteideal an ríomhphoist bhunaidh, agus is féidir leat a fheiceáil gurb é IPV6 an seoladh seoltóra, rud a chiallaíonn go bhfuil IPV6 cumraithe go rathúil freisin.

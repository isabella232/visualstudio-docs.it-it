---
title: Command-Line Capture Tool | Microsoft Docs
description: Informazioni su DXCap.exe, uno strumento da riga di comando per l'acquisizione e la riproduzione di diagnostica della grafica che supporta da Direct3D 10 a Direct3D 12 in tutti i livelli di funzionalità.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: db75b3a7-80b2-4a74-91d2-fd6e0f73b45d
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: b305d2f2f84d4b3f52d9be40f18fe02c9eb93df2
ms.sourcegitcommit: aeed3eb503d0b282537b073ebae8c028c4fef750
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/15/2021
ms.locfileid: "114232713"
---
# <a name="command-line-capture-tool"></a>Strumento di acquisizione da riga di comando
DXCap.exe è uno strumento da riga di comando per l'acquisizione e la riproduzione della diagnostica grafica. Supporta Direct3D dalla versione 10 alla 12 per tutti i livelli di funzionalità.

## <a name="syntax"></a>Sintassi

```cmd
DXCap.exe [-file filename] [-frame frames | -period periods | -manual] -c app [args...]
DXCap.exe -p [filename] [-debug | -warp | -hw] [-config] [-rawmode]
DXCap.exe -p [filename] -screenshot [-frame frames]
DXCap.exe -p [filename] -toXML [xml_filename]
DXCap.exe -v [-file filename] [-examine events] [-haltonfail | -exitonfail] [-showprogress]
DXCap.exe -e [search_string]
DXCap.exe -info
```

#### <a name="parameters"></a>Parametri
 `-file`In modalità di acquisizione ( ) specifica il nome del file di log di grafica in cui vengono registrate `filename` `-c` le informazioni `filename` grafiche. Se `filename` non viene specificato, le informazioni grafiche vengono registrate in un file denominato `<appname>-<date>-<time>.vsglog` per impostazione predefinita.

 In modalità di convalida (-v), `filename` specifica il nome del file di log di grafica da convalidare. Se non viene specificato, viene usato di nuovo il log di grafica convalidato per `filename` l'ultima volta.

 `-frame``frames`In modalità di `frames` acquisizione, specifica i frame da acquisire. Il primo frame è 1. È possibile specificare più frame usando virgole e intervalli. Ad esempio, se `frames` è , vengono acquisiti i frame , , , , e `2, 5, 7-9, 15` `2` `5` `7` `8` `9` `15` .

> [!TIP]
> Usare `-frame` `manual` per specificare che i fotogrammi verranno acquisiti manualmente premendo il tasto Stamp. È possibile acquisire i frame all'avvio dell'app. Per interrompere l'acquisizione dei frame, tornare all'interfaccia della riga di comando e premere INVIO.

 `-period``periods`In modalità di acquisizione `periods` specifica gli intervalli di tempo, in secondi, durante i quali acquisire i frame. È possibile specificare diversi punti usando virgole e intervalli. Ad esempio, se è , vengono acquisiti i frame di cui viene eseguito il rendering tra e secondi e `periods` `2.1-5, 7.0-9.3` tra e `2.1` `5` `7` `9.3` secondi.

 `-c``app`[ `args...` ] Modalità di acquisizione. In modalità di acquisizione, `app` specifica il nome dell'app da cui acquisire le informazioni grafiche; `args...` specifica ulteriori parametri della riga di comando per tale app.

 `-p` [ `filename` ] Modalità di riproduzione ( `-p` ). In modalità di riproduzione, `filename` specifica il nome del file di log di grafica da riprodurre. Se non viene specificato, viene usato di nuovo il log di grafica riprodotto per `filename` l'ultima volta.

 `-debug` In modalità di riproduzione `-debug` specifica che la riproduzione deve essere riprodotta con il livello di debug Direct3D abilitato.

 `-warp` In modalità di riproduzione `-warp` specifica che la riproduzione deve essere riprodotta usando il renderer software WARP.

 `-hw` In modalità di riproduzione specifica `-hw` che la riproduzione deve essere riprodotta usando hardware GPU.

 `-config` In modalità di `-config` riproduzione, visualizza tutte le informazioni sul computer usato per acquisire il file di log di grafica.

 `-rawmode` In modalità di riproduzione `-rawmode` specifica che la riproduzione deve essere eseguita senza apportare modifiche agli eventi registrati. Durante il normale funzionamento, la modalità di riproduzione potrebbe apportare piccole modifiche alla riproduzione per semplificare il debug e velocizzare la riproduzione. Ad esempio, potrebbe simulare l'output della catena di scambio, anziché l'esecuzione dei comandi della catena di scambio. In genere questa riproduzione non è un problema, ma potrebbe essere necessario che la riproduzione venga eseguita in modo più semplice per l'evento registrato. Ad esempio, è possibile usare questa opzione per ripristinare il comportamento di rendering a schermo intero in un'app acquisita durante l'esecuzione in modalità schermo intero.

 `-toXML` [`xml_filename`] In modalità di riproduzione, `xml_filename` specifica il nome del file in cui viene scritta una rappresentazione XML della riproduzione. Se `xml_filename` non viene specificato, la rappresentazione XML viene scritta in un file denominato come il file da riprodurre, ma con l'estensione `.xml`.

 `-v` Modalità di convalida. In modalità di convalida, i frame acquisiti vengono riprodotti sia su dispositivi hardware che WARP e i relativi risultati vengono confrontati mediante una funzione di confronto immagini. È possibile usare questa funzionalità per identificare rapidamente i problemi di driver che interessano il rendering.

 `-examine``events`In modalità di `events` convalida, specifica il set di eventi grafici di cui vengono confrontati i risultati immediati. Ad esempio, `-examine present,draw,copy,clear` limita il confronto solo agli eventi appartenenti a tali categorie.

> [!TIP]
> È consigliabile iniziare con perché questo rivela la maggior parte dei problemi, ma richiede molto meno `-examine present,draw,copy,clear` tempo rispetto a un set più ampio di eventi. Se necessario, è possibile specificare un set di eventi diverso o più grande per convalidare tali eventi e rivelare altri tipi di problemi.

 `-haltonfail` In modalità di convalida, `-haltonfail` interrompe la convalida quando vengono rilevate differenze tra l'hardware e il renderer WARP. Per riprendere la convalida, premere un tasto.

 `-exitonfail` In modalità di convalida, `-exitonfail` termina immediatamente la convalida quando vengono rilevate differenze tra l'hardware e il renderer WARP. Quando il programma viene chiuso in questo modo, torna `0` all'ambiente; in caso contrario, restituisce `1` .

 `-showprogress` In modalità di convalida visualizza `-showprogress` informazioni sullo stato di avanzamento della sessione di convalida. Lo stato WARP viene visualizzato a sinistra; lo stato hardware viene visualizzato a destra.

 `-e``search_string`Enumera le app UWP installate. È possibile usare queste informazioni per eseguire acquisizioni da riga di comando con le app UWP.

 `-info` Visualizza le informazioni sul computer e sulle DLL di acquisizione.

## <a name="remarks"></a>Commenti
 DXCap.exe funziona in tre modalità:

 Modalità di acquisizione (-c) Acquisisce le informazioni grafiche da un'app in esecuzione e le registra in un file di log di grafica. Le funzionalità di acquisizione e il formato di file sono identici a quelli di Visual Studio.

 Modalità di riproduzione (-p) Riproduzione degli eventi grafici acquisiti in precedenza da un file di log di grafica esistente. Per impostazione predefinita, la riproduzione avviene in una finestra, anche quando il file di log di grafica è stato acquisito da un'app a schermo intero. La riproduzione avviene a schermo intero solo quando il file di log di grafica è stato acquisito da un'app a schermo `-rawmode` intero e viene specificato .

 La modalità di convalida ( ) convalida il comportamento di rendering riproducendo i fotogrammi acquisiti sia nell'hardware che in WARP, quindi confrontando i risultati usando una funzione di confronto `-v` delle immagini. È possibile usare questa funzionalità per identificare rapidamente i problemi di driver che interessano il rendering.

 Oltre a queste modalità, dxcap.exe esegue altre due funzioni che non eseguono l'acquisizione o la riproduzione di informazioni grafiche.

 Funzione di enumerazione ( `-e` ) Visualizza i dettagli sulle app UWP installate nel computer. Questi dettagli includono il nome del pacchetto e l'appid che identificano il file eseguibile in un'app UWP. Per acquisire informazioni grafiche da un'app di Windows Store con DXCap.exe, usare il nome del pacchetto e l'ID app anziché il nome del file eseguibile usato durante l'acquisizione di un'app desktop.

 Funzione Info ( `-info)` visualizza i dettagli sul computer e le DLL di acquisizione.

## <a name="examples"></a>Esempio

### <a name="capture-graphics-information-from-a-desktop-app"></a>Acquisizione di informazioni grafiche da un'app desktop
 Usare `-c` per specificare l'app da cui acquisire le informazioni grafiche.

```cmd
DXCap.exe -c BasicHLSL11.exe
```

 Per impostazione predefinita, le informazioni grafiche vengono registrate in un file denominato `<appname>-<date>-<time>.vsglog` . Usare `-file` per specificare un file diverso in cui registrare.

```cmd
DXCap.exe -file regression_test_12.vsglog -c BasicHLSL11.exe
```

 Specificare ulteriori parametri della riga di comando per l'app da cui si esegue l'acquisizione includendoli dopo il nome file dell'app.

```cmd
DXCap.exe -c "C:\Program Files\Internet Explorer\iexplorer.exe" "www.fishgl.com"
```

 Il comando dell'esempio precedente acquisisce informazioni grafiche della versione desktop di Internet Explorer durante la visualizzazione della pagina Web all'indirizzo www.fishgl.com che usa l'API WebGL per il rendering del contenuto in 3D.

> [!NOTE]
> Poiché gli argomenti della riga di comando inseriti dopo l'app vengono passati all'app, è necessario specificare gli argomenti per DXCap.exe prima di usare l'opzione `-c`.

### <a name="capture-graphics-information-from-a-uwp-app"></a>Acquisire informazioni grafiche da un'app UWP.
 È possibile acquisire informazioni grafiche da un'app UWP.

```cmd
DXCap.exe -c Microsof.BingMaps_2.1.2914.1734_x64__8wekyb3d8bbwe,AppexMaps
```

 L'uso di DXCap.exe per l'acquisizione da un'app UWP è simile all'uso per l'acquisizione da un'app desktop Windows, ma l'identificazione di un'app desktop in base al nome file consente di identificare un'app UWP in base al nome del pacchetto e al nome o all'ID del file eseguibile all'interno del pacchetto da cui si vuole eseguire l'acquisizione. Per scoprire più facilmente come identificare le app UWP installate nel computer, usare l'opzione con DXCap.exe `-e` per enumerarle:

```cmd
DXCap.exe -e
```

 È possibile fornire una stringa di ricerca facoltativa per trovare l'app che si sta cercando. Quando viene specificata la stringa di ricerca, DXCap.exe enumera le app UWP il cui nome del pacchetto, il nome dell'app o gli ID app corrispondono alla stringa di ricerca. La ricerca non fa distinzione tra maiuscole e minuscole.

```cmd
DXCap.exe -e map
```

 Il comando precedente enumera le app UWP che corrispondono a "map"; Ecco l'output:

 **Package "Microsoft.BingMaps":** **InstallDirectory : C:\Program Files\WindowsApps\Microsoft.BingMaps_2.1.2914.1734_x64__8wekyb3d8bbwe** **FullName         : Microsoft.BingMaps_2.1.2914.1734_x64__8wekyb3d8bbwe** **UserSID          : S-1-5-21-2127521184-1604012920-1887927527-5603533** **Name             : Microsoft.BingMaps** **Publisher        : CN=Microsoft Corporation, O=Microsoft Corporation, L=Redmond, S=Washington, C=US** **Version          : 2.1.2914.1734** **Launchable Applications:** **Id: AppexMaps** **Exe: C:\Program Files\WindowsApps\Microsoft.BingMaps_2.1.2914.1734_x64__8wekyb3d8bbwe\Map.exe** **IsWWA: No** **AppSpec (to launch): DXCap.exe -c Microsoft.BingMaps_2.1.2914.1734_x64__8wekyb3d8bbwe,AppexMaps** The last line of output for each enumerated app displays the command you can use to capture graphics information from it.

### <a name="capture-specific-frames-or-frames-between-specific-times"></a>Acquisizione di frame specifici o frame tra intervalli di tempo specifici
 Usare per specificare i frame da acquisire usando virgole `-frame` e intervalli:

```cmd
DXCap.exe -frame 2,5,7-9,15 -c SimpleBezier11.exe
```

 In caso contrario, `-period` usare per specificare un set di intervalli di tempo durante i quali acquisire i fotogrammi. Gli intervalli di tempo vengono specificati in secondi ed è possibile indicare più intervalli:

```cmd
DXCap.exe -period 2.1-5, 7.0-9.3 -c SimpleBezier11.exe
```

### <a name="capture-frames-interactively"></a>Acquisizione di frame in modo interattivo
 Usare `-manual` per acquisire i frame in modo interattivo. Premere INVIO per avviare l'acquisizione e premere di nuovo INVIO per interromperla.

```cmd
DXCap.exe -manual -c SimpleBezier11.exe
```

### <a name="play-back-a-graphic-log-file"></a>Riprodurre un file di log grafico
 Usare `-p` per riprodurre un file di log di grafica acquisito in precedenza.

```cmd
DXCap.exe -p regression_test_12.vsglog
```

 Omettere il nome del file per riprodurre il log di grafica acquisito più di recente.

```cmd
DXCap.exe -p
```

### <a name="play-back-in-raw-mode"></a>Riproduzione in modalità raw
 Usare `-rawmode` per riprodurre i comandi acquisiti esattamente come si sono verificati. Nella riproduzione normale, alcuni comandi vengono emulati, ad esempio un file di log di grafica acquisito da un'app a schermo intero verrà riprodotto in una finestra. Se invece è abilitata la modalità raw, lo stesso file verrà riprodotto a schermo intero.

```cmd
DXCap.exe -p regression_test_12.vsglog -rawmode
```

### <a name="play-back-using-warp-or-a-hardware-device"></a>Riproduzione con dispositivo WARP o hardware
 Potrebbe essere necessario forzare la riproduzione di un file di log di grafica acquisito su un dispositivo hardware all'uso di WARP o forzare la riproduzione di un log acquisito su WARP all'uso di un dispositivo hardware. Usare `-warp` per riprodurre con WARP.

```cmd
DXCap.exe -p regression_test_12.vsglog -warp
```

 Usare `-hw` per riprodurre l'hardware.

```cmd
DXCap.exe -p regression_test_12.vsglog -hw
```

### <a name="validate-a-graphics-log-file-against-warp"></a>Convalida di un file di log di grafica per un dispositivo WARP
 In modalità di convalida, il file di log di grafica viene riprodotto sia su dispositivo hardware che WARP confrontando i relativi risultati. Ciò consente di identificare gli errori di rendering causati dal driver. Usare -v per convalidare il comportamento corretto dell'hardware grafico per un dispositivo WARP.

```cmd
DXCap.exe -v regression_test_12.vsglog
```

 Per ridurre la quantità di confronti, è possibile specificare un subset di comandi per la convalida da confrontare e gli altri comandi verranno ignorati. Usare -examine per specificare i comandi di cui confrontare i risultati.

```cmd
DXCap.exe -v regression_test_12.vsglog -examine present,draw,copy,clear
```

### <a name="convert-a-graphics-log-file-to-pngs"></a>Conversione di un file di log di grafica in formato PNG
 Per visualizzare o analizzare i frame da un file di log di grafica, DXCap.exe può salvare i frame acquisiti come file di immagine con estensione PNG (Portable Network Graphics). Usare `-screenshot` per in modalità di riproduzione per l'output dei fotogrammi acquisiti .png file.

```cmd
DXCap.exe -p BasicHLSL11.vsglog -screenshot
```

 Usare `-frame` con per specificare i frame che si desidera visualizzare come `-screenshot` output.

```cmd
DXCap.exe -p BasicHLSL11.vsglog -screenshot -frame 5, 7-9
```

### <a name="convert-a-graphics-log-file-to-xml"></a>Conversione di un file di log di grafica in formato XML
 Per elaborare e analizzare i log di grafica usando strumenti familiari come FindStr o XSLT, DXCap.exe può convertire un file di log di grafica in formato XML. Usare `-toXML` in modalità di riproduzione per convertire il log in XML anziché riprodurlo.

```cmd
DXCap.exe -p regression_test_12.vsglog -toXML
```

 Per impostazione predefinita, l'output XML viene scritto in un file con lo stesso nome del log di grafica, ma con estensione XML. Nell'esempio precedente il file XML sarà denominato **regression_test_12.xml**. Per assegnare un nome diverso al file XML, specificarlo dopo `-toXML` .

```cmd
DXCap.exe -p regression_test_12.vsglog -toXML temp.xml
```

 Il file risultante conterrà un codice XML simile al seguente:

```xml
<Moment value="67"/>
<Method name="CreateDXGIFactory1" >
    <Return type="HRESULT" value="S_OK" />
    <Parameter name="riid" type="IID" value="770AAE78-F26F-4DBA-A829-253C83D1B387" />
    <Parameter name="ppFactory" type="void" handle="1" isOutput="true" />
</Method>

<Moment value="167"/>
<Method name="D3D11CreateDevice" >
    <Return type="HRESULT" value="S_OK" />
    <Parameter name="pAdapter" type="IDXGIAdapter" handle="34" />
    <Parameter name="DriverType" type="D3D_DRIVER_TYPE" value="D3D_DRIVER_TYPE_UNKNOWN" />
    <Parameter name="Software" type="HMODULE" value="pointer" />
    <Parameter name="Flags" type="UINT" value="0" />
    <Parameter name="pFeatureLevels" type="D3D_FEATURE_LEVEL" arrSize="1" >
        <Element value="D3D_FEATURE_LEVEL_11_0" />
    </Parameter>
    <Parameter name="FeatureLevels" type="UINT" value="1" />
    <Parameter name="SDKVersion" type="UINT" value="7" />
    <Parameter name="ppDevice" type="ID3D11Device" handle="35" isOutput="true" />
    <Parameter name="pFeatureLevel" type="D3D_FEATURE_LEVEL" value="D3D_FEATURE_LEVEL_11_0" isOutput="true" />
    <Parameter name="ppImmediateContext" type="ID3D11DeviceContext" value="nullptr" isOutput="true" />
</Method>
```

## <a name="requirements"></a>Requisiti
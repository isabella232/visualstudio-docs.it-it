---
title: '&lt;file&gt; elemento (applicazione ClickOnce) | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- http://www.w3.org/2000/09/xmldsig#Transform
- urn:schemas-microsoft-com:asm.v2#file
- http://www.w3.org/2000/09/xmldsig#DigestValue
- http://www.w3.org/2000/09/xmldsig#DigestMethod
- http://www.w3.org/2000/09/xmldsig#Transforms
- urn:schemas-microsoft-com:asm.v2#hash
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <file> element [ClickOnce application manifest]
- manifests [ClickOnce], file element
ms.assetid: 56e3490c-eed5-4841-b1bf-eefe778b6ac9
caps.latest.revision: 26
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: 16c301d55738519f3e097138f08b6b2c2fe2b4c7
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49270738"
---
# <a name="ltfilegt-element-clickonce-application"></a>&lt;file&gt; elemento (applicazione ClickOnce)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Identifica tutti i file scaricata e usata dall'applicazione.  
  
## <a name="syntax"></a>Sintassi  
  
```  
<file  
    name  
    size  
    group  
    optional  
    writeableType  
>  
    <typelib  
        tlbid  
        version  
        helpdir  
        resourceid  
        flags  
    />  
    <comClass  
        clsid  
        description  
        threadingModel  
        tlbid  
        progid  
        miscStatus  
        miscStatusIcon  
        miscStatusContent  
        miscStatusDocPrint  
        miscStatusThumbnail  
    />  
    <comInterfaceExternalProxyStub  
        iid  
        baseInterface  
        numMethods  
        name  
        tlbid  
        proxyStubClass32  
    />  
    <comInterfaceProxyStub  
        iid  
        baseInterface  
        numMethods  
        name  
        tlbid  
        proxyStubClass32  
    />  
    <windowClass  
        versioned  
    />  
</file>  
```  
  
## <a name="elements-and-attributes"></a>Elementi e attributi  
 L'elemento `file` è facoltativo. L'elemento ha gli attributi seguenti.  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|`name`|Obbligatorio. Identifica il nome del file.|  
|`size`|Obbligatorio. Specifica la dimensione, espressa in byte, del file.|  
|`group`|Facoltativo, se il `optional` attributo viene omesso o impostato su `false`; se necessario `optional` è `true`. Il nome del gruppo a cui appartiene questo file. Il nome può essere qualsiasi valore di stringa Unicode scelta dallo sviluppatore e viene usato per il download dei file su richiesta con il <xref:System.Deployment.Application.ApplicationDeployment> classe.|  
|`optional`|Facoltativo. Specifica se il file deve essere download quando l'applicazione è la prima esecuzione, o se il file deve risiedere solo nel server fino a quando non viene richiesto dall'applicazione su richiesta. Se `false` o non definito, il file viene scaricato quando l'applicazione o della prima esecuzione installata. Se `true`, un `group` deve essere specificato per il manifesto dell'applicazione sia valido. `optional` non può essere true se `writeableType` viene specificato con il valore `applicationData`.|  
|`writeableType`|Facoltativo. Specifica che questo file è un file di dati. Attualmente l'unico valore valido è `applicationData`.|  
  
## <a name="typelib"></a>libreria dei tipi  
 Il `typelib` elemento è un elemento figlio facoltativo dell'elemento file. L'elemento descrive la libreria dei tipi a cui appartiene il componente COM. L'elemento ha gli attributi seguenti.  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|`tlbid`|Obbligatorio. GUID assegnato alla libreria dei tipi.|  
|`version`|Obbligatorio. Il numero di versione della libreria dei tipi.|  
|`helpdir`|Obbligatorio. La directory che contiene i file della Guida per il componente. Potrebbe essere a lunghezza zero.|  
|`resourceid`|Facoltativo. Rappresentazione di stringa esadecimale dell'identificatore delle impostazioni locali (LCID). È uno a quattro cifre esadecimali senza il prefisso 0x e senza zeri iniziali. L'identificatore LCID può avere un identificatore di varietà di lingua neutra.|  
|`flags`|Facoltativo. La rappresentazione di stringa dei flag della libreria di tipo per questa libreria dei tipi. In particolare, deve essere uno dei "RESTRICTED", "Controllo", "HIDDEN" e "HASDISKIMAGE".|  
  
## <a name="comclass"></a>comClass  
 Il `comClass` costituisce un elemento figlio facoltativo di `file` elemento, ma è obbligatorio se il [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] applicazione contiene un componente COM che si desidera distribuire mediante COM senza registrazione. L'elemento ha gli attributi seguenti.  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|`clsid`|Obbligatorio. L'ID di classe del componente COM espresso come GUID.|  
|`description`|Facoltativo. Nome della classe.|  
|`threadingModel`|Facoltativo. Il modello di threading utilizzato dalle classi COM nel processo. Se questa proprietà è null, non viene utilizzato alcun modello di threading. Il componente viene creato nel thread principale del client e vengono effettuato il marshalling di chiamate da altri thread per questo thread. L'elenco seguente mostra i valori validi:<br /><br /> `Apartment`, `Free`, `Both`e `Neutral`.|  
|`tlbid`|Facoltativo. GUID della libreria dei tipi per il componente COM.|  
|`progid`|Facoltativo. Identificatore a livello di codice dipendente dalla versione associati al componente COM. Il formato di un `ProgID` è `<vendor>.<component>.<version>`.|  
|`miscStatus`|Facoltativo. I duplicati nell'assembly manifesto le informazioni fornite dal `MiscStatus` chiave del Registro di sistema. Se i valori per il `miscStatusIcon`, `miscStatusContent`, `miscStatusDocprint`, o `miscStatusThumbnail` gli attributi non vengono trovati, il corrispondente valore predefinito elencato nella `miscStatus` viene usato per gli attributi mancanti. Il valore può essere un elenco delimitato da virgole dei valori dell'attributo nella tabella seguente. È possibile usare questo attributo se la classe COM è una classe OCX che richiede `MiscStatus` valori di chiave del Registro di sistema.|  
|`miscStatusIcon`|Facoltativo. I duplicati nell'assembly del manifesto le informazioni fornite da DVASPECT_ICON. Fornisce un'icona di un oggetto. Il valore può essere un elenco delimitato da virgole dei valori dell'attributo nella tabella seguente. È possibile usare questo attributo se la classe COM è una classe OCX che richiede `Miscstatus` valori di chiave del Registro di sistema.|  
|`miscStatusContent`|Facoltativo. I duplicati nell'assembly del manifesto le informazioni fornite da DVASPECT_CONTENT. È possibile fornire un documento composito visualizzabile per un monitor o una stampante. Il valore può essere un elenco delimitato da virgole dei valori dell'attributo nella tabella seguente. È possibile usare questo attributo se la classe COM è una classe OCX che richiede `MiscStatus` valori di chiave del Registro di sistema.|  
|`miscStatusDocPrint`|Facoltativo. I duplicati nell'assembly del manifesto le informazioni fornite da DVASPECT_DOCPRINT. Fornisce una rappresentazione di oggetto visualizzabile sullo schermo come se inviato a una stampante. Il valore può essere un elenco delimitato da virgole dei valori dell'attributo nella tabella seguente. È possibile usare questo attributo se la classe COM è una classe OCX che richiede `MiscStatus` valori di chiave del Registro di sistema.|  
|`miscStatusThumbnail`|Facoltativo. I duplicati in un assembly manifesto le informazioni fornite da DVASPECT_THUMBNAIL. Fornisce un'anteprima di un oggetto visualizzabile in uno strumento di esplorazione. Il valore può essere un elenco delimitato da virgole dei valori dell'attributo nella tabella seguente. È possibile usare questo attributo se la classe COM è una classe OCX che richiede `MiscStatus` valori di chiave del Registro di sistema.|  
  
## <a name="cominterfaceexternalproxystub"></a>comInterfaceExternalProxyStub  
 Il `comInterfaceExternalProxyStub` costituisce un elemento figlio facoltativo di `file` elemento, ma potrebbe essere necessario se il [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] applicazione contiene un componente COM che si desidera distribuire mediante COM senza registrazione. L'elemento contiene gli attributi seguenti.  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|`iid`|Obbligatorio. L'ID interfaccia (IID) che verrà servita da questo proxy. IID deve avere tra parentesi quadre.|  
|`baseInterface`|Facoltativo. IID dell'interfaccia da cui l'interfaccia fa `iid` è derivato.|  
|`numMethods`|Facoltativo. Il numero di metodi implementati dall'interfaccia.|  
|`name`|Facoltativo. Il nome dell'interfaccia che verrà visualizzato nel codice.|  
|`tlbid`|Facoltativo. La libreria dei tipi che contiene la descrizione dell'interfaccia specificata per il `iid` attributo.|  
|`proxyStubClass32`|Facoltativo. Esegue il mapping di un IID a un CLSID nelle DLL proxy a 32 bit.|  
  
## <a name="cominterfaceproxystub"></a>comInterfaceProxyStub  
 Il `comInterfaceProxyStub` costituisce un elemento figlio facoltativo di `file` elemento, ma potrebbe essere necessario se il [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] applicazione contiene un componente COM che si desidera distribuire mediante COM senza registrazione. L'elemento contiene gli attributi seguenti.  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|`iid`|Obbligatorio. L'ID interfaccia (IID) che verrà servita da questo proxy. IID deve avere tra parentesi quadre.|  
|`baseInterface`|Facoltativo. IID dell'interfaccia da cui l'interfaccia fa `iid` è derivato.|  
|`numMethods`|Facoltativo. Il numero di metodi implementati dall'interfaccia.|  
|`Name`|Facoltativo. Il nome dell'interfaccia che verrà visualizzato nel codice.|  
|`Tlbid`|Facoltativo. La libreria dei tipi che contiene la descrizione dell'interfaccia specificata per il `iid` attributo.|  
|`proxyStubClass32`|Facoltativo. Esegue il mapping di un IID a un CLSID nelle DLL proxy a 32 bit.|  
|`threadingModel`|Facoltativo. Facoltativo. Il modello di threading utilizzato dalle classi COM nel processo. Se questa proprietà è null, non viene utilizzato alcun modello di threading. Il componente viene creato nel thread principale del client e vengono effettuato il marshalling di chiamate da altri thread per questo thread. L'elenco seguente mostra i valori validi:<br /><br /> `Apartment`, `Free`, `Both`e `Neutral`.|  
  
## <a name="windowclass"></a>windowClass  
 Il `windowClass` costituisce un elemento figlio facoltativo di `file` elemento, ma potrebbe essere necessario se il [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] applicazione contiene un componente COM che si desidera distribuire mediante COM senza registrazione. L'elemento fa riferimento a una classe di finestra definita dal componente COM che deve essere installata una versione applicato. L'elemento contiene gli attributi seguenti.  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|`versioned`|Facoltativo. Controlla se la finestra interna classe nome usato nella registrazione contiene la versione dell'assembly che contiene la classe della finestra. Il valore di questo attributo può essere `yes` o `no`. Il valore predefinito è `yes`. Il valore `no` deve essere utilizzato solo se la stessa classe della finestra è definita da un componente side-by-side ed un'equivalente non-side-by-side e si desidera trattarli come la classe della finestra stessa. Si noti che si applicano le regole normali sulla registrazione delle classi di finestra, ovvero solo il primo componente che registra la classe di finestra saranno in grado di registrare, perché non dispone di una versione applicata.|  
  
## <a name="hash"></a>hash  
 Il `hash` costituisce un elemento figlio facoltativo di `file` elemento. L'elemento `hash` non ha attributi.  
  
 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] Usa un hash algoritmico di tutti i file in un'applicazione come un controllo di sicurezza, per assicurarsi che nessuno dei file sono stati modificati dopo la distribuzione. Se il `hash` elemento non è incluso, questo controllo non verrà eseguito. Pertanto, l'omissione di `hash` elemento non è consigliato.  
  
 Se un manifesto contiene un file che non è stato eseguito l'hashing, tale manifesto non può essere digitale firmato, perché gli utenti non è possibile verificare il contenuto di un file senza hash.  
  
## <a name="dsigtransforms"></a>dsig: Transforms  
 Il `dsig:Transforms` elemento è un elemento figlio obbligatorio del `hash` elemento. L'elemento `dsig:Transforms` non ha attributi.  
  
## <a name="dsigtransform"></a>dsig: Transform  
 Il `dsig:Transform` elemento è un elemento figlio obbligatorio del `dsig:Transforms` elemento. L'elemento `dsig:Transform` presenta gli attributi seguenti.  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|`Algorithm`|L'algoritmo utilizzato per la quale calcolare il digest per questo file. Attualmente l'unico valore usato da [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] è `urn:schemas-microsoft-com:HashTransforms.Identity`.|  
  
## <a name="dsigdigestmethod"></a>dsig: DigestMethod  
 Il `dsig:DigestMethod` elemento è un elemento figlio obbligatorio del `hash` elemento. L'elemento `dsig:DigestMethod` presenta gli attributi seguenti.  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|`Algorithm`|L'algoritmo utilizzato per la quale calcolare il digest per questo file. Attualmente l'unico valore usato da [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] è `http://www.w3.org/2000/09/xmldsig#sha1`.|  
  
## <a name="dsigdigestvalue"></a>dsig:  
 Il `dsig:DigestValue` elemento è un elemento figlio obbligatorio del `hash` elemento. L'elemento `dsig:DigestValue` non ha attributi. Il valore di testo è l'hash calcolato per il file specificato.  
  
## <a name="remarks"></a>Note  
 Questo elemento identifica tutti gli i file che costituiscono l'applicazione e, in particolare, i valori hash per la verifica dei file. Questo elemento può includere anche i dati sull'isolamento modello COM (Component Object) associati al file. Se viene modificato un file, file manifesto dell'applicazione deve inoltre essere aggiornato per riflettere la modifica.  
  
## <a name="example"></a>Esempio  
 L'esempio di codice seguente illustra `file` elementi in un'applicazione del manifesto per un'applicazione distribuita usando [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)].  
  
```  
<file name="Icon.ico" size="9216">  
  <hash>  
    <dsig:Transforms>  
      <dsig:Transform Algorithm="urn:schemas-microsoft-com:HashTransforms.Identity" />  
    </dsig:Transforms>  
    <dsig:DigestMethod Algorithm="http://www.w3.org/2000/09/xmldsig#sha1" />  
    <dsig:DigestValue>lVoj+Rh6RQ/HPNLOdayQah5McrI=</dsig:DigestValue>  
  </hash>  
</file>  
```  
  
## <a name="see-also"></a>Vedere anche  
 [ClickOnce Application Manifest](../deployment/clickonce-application-manifest.md)




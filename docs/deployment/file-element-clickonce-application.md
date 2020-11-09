---
title: '&lt;&gt;elemento file (applicazione ClickOnce) | Microsoft Docs'
description: L'elemento file identifica tutti i file non di assembly scaricati e utilizzati dall'applicazione. L'elemento file è facoltativo.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9a4d09d4a0e141359b066f2af31c158f36c96522
ms.sourcegitcommit: 0893244403aae9187c9375ecf0e5c221c32c225b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/09/2020
ms.locfileid: "94382741"
---
# <a name="ltfilegt-element-clickonce-application"></a>&lt;&gt;elemento file (applicazione ClickOnce)
Identifica tutti i file non di assembly scaricati e utilizzati dall'applicazione.

## <a name="syntax"></a>Sintassi

```xml
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
 L'elemento `file` è facoltativo. L'elemento presenta gli attributi seguenti.

|Attributo|Descrizione|
|---------------|-----------------|
|`name`|Obbligatorio. Identifica il nome del file.|
|`size`|Obbligatorio. Specifica la dimensione, in byte, del file.|
|`group`|Facoltativo, se l' `optional` attributo non è specificato o impostato su `false` ; obbligatorio se `optional` è `true` . Nome del gruppo a cui appartiene il file. Il nome può essere qualsiasi valore stringa Unicode scelto dallo sviluppatore e viene usato per il download di file su richiesta con la <xref:System.Deployment.Application.ApplicationDeployment> classe.|
|`optional`|Facoltativa. Specifica se il file deve essere scaricato quando l'applicazione viene eseguita per la prima volta o se il file deve risiedere solo sul server fino a quando l'applicazione lo richiede su richiesta. Se `false` o non definito, il file viene scaricato quando l'applicazione viene eseguita per la prima volta o installata. Se `true` , è `group` necessario specificare un oggetto affinché il manifesto dell'applicazione sia valido. `optional` non può essere true se `writeableType` viene specificato con il valore `applicationData` .|
|`writeableType`|Facoltativa. Specifica che il file è un file di dati. Attualmente, l'unico valore valido è `applicationData`.|

## <a name="typelib"></a>typelib
 L' `typelib` elemento è un elemento figlio facoltativo dell'elemento file. L'elemento descrive la libreria dei tipi che appartiene al componente COM. L'elemento presenta gli attributi seguenti.

|Attributo|Descrizione|
|---------------|-----------------|
|`tlbid`|Obbligatorio. GUID assegnato alla libreria dei tipi.|
|`version`|Obbligatorio. Numero di versione della libreria dei tipi.|
|`helpdir`|Obbligatorio. Directory che contiene i file della Guida per il componente. Può essere di lunghezza zero.|
|`resourceid`|Facoltativa. Rappresentazione in forma di stringa esadecimale dell'identificatore delle impostazioni locali (LCID). Si tratta di una a quattro cifre esadecimali senza prefisso 0x e senza zeri iniziali. L'identificatore LCID può avere un identificatore di sottolingua neutro.|
|`flags`|Facoltativa. Rappresentazione di stringa dei flag della libreria dei tipi per questa libreria dei tipi. In particolare, deve essere uno dei "Restricted", "CONTROL", "HIDDEN" e "HASDISKIMAGE".|

## <a name="comclass"></a>comClass
 L' `comClass` elemento è un elemento figlio facoltativo dell' `file` elemento, ma è obbligatorio se l' [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] applicazione contiene un componente COM che intende distribuire utilizzando com senza registrazione. L'elemento presenta gli attributi seguenti.

|Attributo|Descrizione|
|---------------|-----------------|
|`clsid`|Obbligatorio. ID di classe del componente COM espresso come GUID.|
|`description`|Facoltativa. Nome della classe.|
|`threadingModel`|Facoltativa. Modello di threading utilizzato dalle classi COM in-process. Se questa proprietà è null, non viene utilizzato alcun modello di Threading. Il componente viene creato nel thread principale del client e viene effettuato il marshalling di chiamate da altri thread a questo thread. Nell'elenco seguente sono riportati i valori validi:<br /><br /> `Apartment`, `Free`, `Both` e `Neutral`.|
|`tlbid`|Facoltativa. GUID della libreria dei tipi per il componente COM.|
|`progid`|Facoltativa. Identificatore a livello di codice dipendente dalla versione associato al componente COM. Il formato di un oggetto `ProgID` è `<vendor>.<component>.<version>` .|
|`miscStatus`|Facoltativa. I duplicati nell'assembly manifesteranno le informazioni fornite dalla `MiscStatus` chiave del registro di sistema. Se i valori degli `miscStatusIcon` `miscStatusContent` attributi,, `miscStatusDocprint` o `miscStatusThumbnail` non vengono trovati, `miscStatus` per gli attributi mancanti viene usato il valore predefinito corrispondente elencato in. Il valore può essere un elenco delimitato da virgole dei valori di attributo della tabella seguente. È possibile utilizzare questo attributo se la classe COM è una classe OCX che richiede `MiscStatus` valori di chiave del registro di sistema.|
|`miscStatusIcon`|Facoltativa. Duplicati nel manifesto dell'assembly le informazioni fornite da DVASPECT_ICON. Può fornire un'icona di un oggetto. Il valore può essere un elenco delimitato da virgole dei valori di attributo della tabella seguente. È possibile utilizzare questo attributo se la classe COM è una classe OCX che richiede `Miscstatus` valori di chiave del registro di sistema.|
|`miscStatusContent`|Facoltativa. Duplicati nel manifesto dell'assembly le informazioni fornite da DVASPECT_CONTENT. Può fornire un documento composito visualizzabile per una schermata o una stampante. Il valore può essere un elenco delimitato da virgole dei valori di attributo della tabella seguente. È possibile utilizzare questo attributo se la classe COM è una classe OCX che richiede `MiscStatus` valori di chiave del registro di sistema.|
|`miscStatusDocPrint`|Facoltativa. Duplicati nel manifesto dell'assembly le informazioni fornite da DVASPECT_DOCPRINT. Può fornire una rappresentazione dell'oggetto visualizzabile sullo schermo come se fosse stampata su una stampante. Il valore può essere un elenco delimitato da virgole dei valori di attributo della tabella seguente. È possibile utilizzare questo attributo se la classe COM è una classe OCX che richiede `MiscStatus` valori di chiave del registro di sistema.|
|`miscStatusThumbnail`|Facoltativa. Duplicati nel manifesto di un assembly le informazioni fornite da DVASPECT_THUMBNAIL. Può fornire un'anteprima di un oggetto visualizzabile in uno strumento di esplorazione. Il valore può essere un elenco delimitato da virgole dei valori di attributo della tabella seguente. È possibile utilizzare questo attributo se la classe COM è una classe OCX che richiede `MiscStatus` valori di chiave del registro di sistema.|

## <a name="cominterfaceexternalproxystub"></a>comInterfaceExternalProxyStub
 L' `comInterfaceExternalProxyStub` elemento è un elemento figlio facoltativo dell' `file` elemento, ma può essere necessario se l' [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] applicazione contiene un componente COM che intende distribuire utilizzando com senza registrazione. L'elemento contiene gli attributi seguenti.

|Attributo|Descrizione|
|---------------|-----------------|
|`iid`|Obbligatorio. ID di interfaccia (IID) servito dal proxy. L'IID deve contenere parentesi graffe.|
|`baseInterface`|Facoltativa. IID dell'interfaccia da cui deriva l'interfaccia a cui fa riferimento `iid` .|
|`numMethods`|Facoltativa. Numero di metodi implementati dall'interfaccia.|
|`name`|Facoltativa. Nome dell'interfaccia come verrà visualizzato nel codice.|
|`tlbid`|Facoltativa. Libreria dei tipi che contiene la descrizione dell'interfaccia specificata dall' `iid` attributo.|
|`proxyStubClass32`|Facoltativa. Esegue il mapping di un IID a un CLSID in DLL proxy a 32 bit.|

## <a name="cominterfaceproxystub"></a>comInterfaceProxyStub
 L' `comInterfaceProxyStub` elemento è un elemento figlio facoltativo dell' `file` elemento, ma può essere necessario se l' [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] applicazione contiene un componente COM che intende distribuire utilizzando com senza registrazione. L'elemento contiene gli attributi seguenti.

|Attributo|Descrizione|
|---------------|-----------------|
|`iid`|Obbligatorio. ID di interfaccia (IID) servito dal proxy. L'IID deve contenere parentesi graffe.|
|`baseInterface`|Facoltativa. IID dell'interfaccia da cui deriva l'interfaccia a cui fa riferimento `iid` .|
|`numMethods`|Facoltativa. Numero di metodi implementati dall'interfaccia.|
|`Name`|Facoltativa. Nome dell'interfaccia come verrà visualizzato nel codice.|
|`Tlbid`|Facoltativa. Libreria dei tipi che contiene la descrizione dell'interfaccia specificata dall' `iid` attributo.|
|`proxyStubClass32`|Facoltativa. Esegue il mapping di un IID a un CLSID in DLL proxy a 32 bit.|
|`threadingModel`|Facoltativa. Facoltativa. Modello di threading utilizzato dalle classi COM in-process. Se questa proprietà è null, non viene utilizzato alcun modello di Threading. Il componente viene creato nel thread principale del client e viene effettuato il marshalling di chiamate da altri thread a questo thread. Nell'elenco seguente sono riportati i valori validi:<br /><br /> `Apartment`, `Free`, `Both` e `Neutral`.|

## <a name="windowclass"></a>windowClass
 L' `windowClass` elemento è un elemento figlio facoltativo dell' `file` elemento, ma può essere necessario se l' [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] applicazione contiene un componente COM che intende distribuire utilizzando com senza registrazione. L'elemento fa riferimento a una classe di finestra definita dal componente COM a cui è necessario applicare una versione. L'elemento contiene gli attributi seguenti.

|Attributo|Descrizione|
|---------------|-----------------|
|`versioned`|Facoltativa. Controlla se il nome della classe interna della finestra utilizzato nella registrazione contiene la versione dell'assembly che contiene la classe della finestra. Il valore di questo attributo può essere `yes` o `no` . Il valore predefinito è `yes`. Il valore `no` deve essere usato solo se la stessa classe di finestra è definita da un componente affiancato e da un componente non affiancato equivalente e si desidera considerarli come la stessa classe di finestra. Si noti che le normali regole relative alla registrazione della classe di finestra sono valide. solo il primo componente che registra la classe di finestra sarà in grado di registrarlo, perché non è stata applicata una versione.|

## <a name="hash"></a>hash
 L' `hash` elemento è un elemento figlio facoltativo dell' `file` elemento. L'elemento `hash` non ha attributi.

 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Usa un hash algoritmico di tutti i file di un'applicazione come controllo di sicurezza, per garantire che nessuno dei file sia stato modificato dopo la distribuzione. Se l' `hash` elemento non è incluso, questo controllo non verrà eseguito. Non è pertanto consigliabile omettere l' `hash` elemento.

 Se un manifesto contiene un file di cui non è stato eseguito l'hashing, il manifesto non può essere firmato digitalmente, perché gli utenti non possono verificare il contenuto di un file senza hash.

## <a name="dsigtransforms"></a>dsig:Transforms
 L' `dsig:Transforms` elemento è un figlio obbligatorio dell' `hash` elemento. L'elemento `dsig:Transforms` non ha attributi.

## <a name="dsigtransform"></a>dsig:Transform
 L' `dsig:Transform` elemento è un figlio obbligatorio dell' `dsig:Transforms` elemento. L'elemento `dsig:Transform` presenta gli attributi seguenti.

| Attributo | Descrizione |
|-------------| - |
| `Algorithm` | Algoritmo utilizzato per calcolare il digest per il file. Attualmente l'unico valore utilizzato da [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] è `urn:schemas-microsoft-com:HashTransforms.Identity` . |

## <a name="dsigdigestmethod"></a>dsig: DigestMethod
 L' `dsig:DigestMethod` elemento è un figlio obbligatorio dell' `hash` elemento. L'elemento `dsig:DigestMethod` presenta gli attributi seguenti.

| Attributo | Descrizione |
|-------------| - |
| `Algorithm` | Algoritmo utilizzato per calcolare il digest per il file. Attualmente l'unico valore utilizzato da [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] è `http://www.w3.org/2000/09/xmldsig#sha1` . |

## <a name="dsigdigestvalue"></a>dsig: DigestValue
 L' `dsig:DigestValue` elemento è un figlio obbligatorio dell' `hash` elemento. L'elemento `dsig:DigestValue` non ha attributi. Il valore di testo è l'hash calcolato per il file specificato.

## <a name="remarks"></a>Commenti
 Questo elemento identifica tutti i file non di assembly che costituiscono l'applicazione e, in particolare, i valori hash per la verifica dei file. Questo elemento può includere anche Component Object Model dati di isolamento (COM) associati al file. Se un file viene modificato, è necessario aggiornare anche il file manifesto dell'applicazione in modo da riflettere la modifica.

## <a name="example"></a>Esempio
 Nell'esempio di codice seguente vengono illustrati `file` gli elementi in un manifesto dell'applicazione per un'applicazione distribuita tramite [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] .

```xml
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
- [Manifesto dell'applicazione ClickOnce](../deployment/clickonce-application-manifest.md)
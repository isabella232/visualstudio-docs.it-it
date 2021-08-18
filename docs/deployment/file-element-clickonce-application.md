---
title: '&lt;Elemento file &gt; (ClickOnce Application) | Microsoft Docs'
description: L'elemento file identifica tutti i file non assembly scaricati e usati dall'applicazione. L'elemento file è facoltativo.
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
manager: jmartens
ms.technology: vs-ide-deployment
ms.workload:
- multiple
ms.openlocfilehash: 68733629b26b4640e63919aaa4f9d07d0c70f972
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122051599"
---
# <a name="ltfilegt-element-clickonce-application"></a>&lt;Elemento file &gt; (ClickOnce app)
Identifica tutti i file non assembly scaricati e usati dall'applicazione.

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
|`size`|Obbligatorio. Specifica le dimensioni, in byte, del file.|
|`group`|Facoltativo, se `optional` l'attributo non è specificato o impostato su `false` ; obbligatorio se `optional` è `true` . Nome del gruppo a cui appartiene il file. Il nome può essere qualsiasi valore di stringa Unicode scelto dallo sviluppatore e viene usato per scaricare file su richiesta con la <xref:System.Deployment.Application.ApplicationDeployment> classe .|
|`optional`|facoltativo. Specifica se il file deve essere scaricato alla prima esecuzione dell'applicazione o se il file deve risiedere solo nel server fino a quando l'applicazione non lo richiede su richiesta. Se `false` o non è definito, il file viene scaricato alla prima esecuzione o installazione dell'applicazione. Se `true` , è necessario specificare un oggetto perché il manifesto `group` dell'applicazione sia valido. `optional` non può essere true se `writeableType` è specificato con il valore `applicationData` .|
|`writeableType`|facoltativo. Specifica che questo file è un file di dati. Attualmente, l'unico valore valido è `applicationData`.|

## <a name="typelib"></a>typelib
 `typelib`L'elemento è un elemento figlio facoltativo dell'elemento file. L'elemento descrive la libreria dei tipi che appartiene al componente COM. L'elemento presenta gli attributi seguenti.

|Attributo|Descrizione|
|---------------|-----------------|
|`tlbid`|Obbligatorio. GUID assegnato alla libreria dei tipi.|
|`version`|Obbligatorio. Numero di versione della libreria dei tipi.|
|`helpdir`|Obbligatorio. Directory che contiene i file della Guida per il componente. Può essere di lunghezza zero.|
|`resourceid`|facoltativo. Rappresentazione di stringa esadecimale dell'identificatore delle impostazioni locali (LCID). Si tratta di una o quattro cifre esadecimali senza un prefisso 0x e senza zeri iniziali. L'identificatore LCID può avere un identificatore di sottolinguaggio neutro.|
|`flags`|facoltativo. Rappresentazione di stringa dei flag della libreria dei tipi per questa libreria dei tipi. In particolare, deve essere tra "RESTRICTED", "CONTROL", "HIDDEN" e "HASDISKIMAGE".|

## <a name="comclass"></a>comClass
 L'elemento è un elemento figlio facoltativo dell'elemento , ma è obbligatorio se l'applicazione contiene un componente COM che intende distribuire `comClass` `file` usando COM senza [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] registrazione. L'elemento presenta gli attributi seguenti.

|Attributo|Descrizione|
|---------------|-----------------|
|`clsid`|Obbligatorio. ID di classe del componente COM espresso come GUID.|
|`description`|facoltativo. Nome della classe.|
|`threadingModel`|facoltativo. Modello di threading usato dalle classi COM in-process. Se questa proprietà è Null, non viene usato alcun modello di threading. Il componente viene creato nel thread principale del client e viene effettuato il marshalling delle chiamate da altri thread a questo thread. L'elenco seguente mostra i valori validi:<br /><br /> `Apartment`, `Free`, `Both` e `Neutral`.|
|`tlbid`|facoltativo. GUID per la libreria dei tipi per questo componente COM.|
|`progid`|facoltativo. Identificatore a livello di codice dipendente dalla versione associato al componente COM. Il formato di è `ProgID` `<vendor>.<component>.<version>` .|
|`miscStatus`|facoltativo. Duplica nel manifesto dell'assembly le informazioni fornite dalla chiave `MiscStatus` del Registro di sistema. Se i valori per gli attributi , , o non vengono trovati, per gli attributi mancanti viene usato il valore predefinito corrispondente `miscStatusIcon` `miscStatusContent` `miscStatusDocprint` `miscStatusThumbnail` `miscStatus` elencato in . Il valore può essere un elenco delimitato da virgole dei valori degli attributi della tabella seguente. È possibile usare questo attributo se la classe COM è una classe OCX che richiede valori di `MiscStatus` chiave del Registro di sistema.|
|`miscStatusIcon`|facoltativo. Duplica nel manifesto dell'assembly le informazioni fornite DVASPECT_ICON. Può fornire un'icona di un oggetto . Il valore può essere un elenco delimitato da virgole dei valori degli attributi della tabella seguente. È possibile usare questo attributo se la classe COM è una classe OCX che richiede valori di `Miscstatus` chiave del Registro di sistema.|
|`miscStatusContent`|facoltativo. Duplica nel manifesto dell'assembly le informazioni fornite DVASPECT_CONTENT. Può fornire un documento composto visualizzabile per uno schermo o una stampante. Il valore può essere un elenco delimitato da virgole dei valori degli attributi della tabella seguente. È possibile usare questo attributo se la classe COM è una classe OCX che richiede valori di `MiscStatus` chiave del Registro di sistema.|
|`miscStatusDocPrint`|facoltativo. Duplica nel manifesto dell'assembly le informazioni fornite DVASPECT_DOCPRINT. Può fornire una rappresentazione dell'oggetto visualizzabile sullo schermo come se fosse stampata su una stampante. Il valore può essere un elenco delimitato da virgole dei valori degli attributi della tabella seguente. È possibile usare questo attributo se la classe COM è una classe OCX che richiede valori di `MiscStatus` chiave del Registro di sistema.|
|`miscStatusThumbnail`|facoltativo. Duplica in un manifesto dell'assembly le informazioni fornite da DVASPECT_THUMBNAIL. Può fornire un'anteprima di un oggetto visualizzabile in uno strumento di esplorazione. Il valore può essere un elenco delimitato da virgole dei valori degli attributi della tabella seguente. È possibile usare questo attributo se la classe COM è una classe OCX che richiede valori di `MiscStatus` chiave del Registro di sistema.|

## <a name="cominterfaceexternalproxystub"></a>comInterfaceExternalProxyStub
 L'elemento è un elemento figlio facoltativo dell'elemento , ma può essere obbligatorio se l'applicazione contiene un componente COM che intende distribuire usando COM senza `comInterfaceExternalProxyStub` `file` [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] registrazione. L'elemento contiene gli attributi seguenti.

|Attributo|Descrizione|
|---------------|-----------------|
|`iid`|Obbligatorio. ID di interfaccia (IID) servito da questo proxy. L'IID deve contenere parentesi graffe che lo circondano.|
|`baseInterface`|facoltativo. IID dell'interfaccia da cui deriva l'interfaccia a cui fa `iid` riferimento .|
|`numMethods`|facoltativo. Numero di metodi implementati dall'interfaccia .|
|`name`|facoltativo. Nome dell'interfaccia così come verrà visualizzata nel codice.|
|`tlbid`|facoltativo. Libreria dei tipi che contiene la descrizione dell'interfaccia specificata `iid` dall'attributo .|
|`proxyStubClass32`|facoltativo. Mappe un IID a un CLSID nelle DLL proxy a 32 bit.|

## <a name="cominterfaceproxystub"></a>comInterfaceProxyStub
 L'elemento è un elemento figlio facoltativo dell'elemento , ma può essere obbligatorio se l'applicazione contiene un componente COM che intende distribuire usando COM senza `comInterfaceProxyStub` `file` [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] registrazione. L'elemento contiene gli attributi seguenti.

|Attributo|Descrizione|
|---------------|-----------------|
|`iid`|Obbligatorio. ID di interfaccia (IID) che viene servito da questo proxy. L'IID deve contenere parentesi graffe che lo circondano.|
|`baseInterface`|facoltativo. IID dell'interfaccia da cui deriva l'interfaccia a cui fa `iid` riferimento .|
|`numMethods`|facoltativo. Numero di metodi implementati dall'interfaccia .|
|`Name`|facoltativo. Nome dell'interfaccia così come verrà visualizzata nel codice.|
|`Tlbid`|facoltativo. Libreria dei tipi che contiene la descrizione dell'interfaccia specificata `iid` dall'attributo .|
|`proxyStubClass32`|facoltativo. Mappe un IID a un CLSID nelle DLL proxy a 32 bit.|
|`threadingModel`|facoltativo. facoltativo. Modello di threading utilizzato dalle classi COM in-process. Se questa proprietà è Null, non viene usato alcun modello di threading. Il componente viene creato nel thread principale del client e viene effettuato il marshalling delle chiamate da altri thread a questo thread. L'elenco seguente mostra i valori validi:<br /><br /> `Apartment`, `Free`, `Both` e `Neutral`.|

## <a name="windowclass"></a>windowClass
 L'elemento è un elemento figlio facoltativo dell'elemento , ma può essere obbligatorio se l'applicazione contiene un componente COM che intende distribuire usando COM senza `windowClass` `file` [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] registrazione. L'elemento fa riferimento a una classe di finestra definita dal componente COM a cui deve essere applicata una versione. L'elemento contiene gli attributi seguenti.

|Attributo|Descrizione|
|---------------|-----------------|
|`versioned`|Facoltativa. Controlla se il nome della classe della finestra interna utilizzato nella registrazione contiene la versione dell'assembly che contiene la classe della finestra. Il valore di questo attributo può essere `yes` o `no` . Il valore predefinito è `yes`. Il valore deve essere usato solo se la stessa classe di finestra è definita da un componente affiancato e da un componente non affiancato equivalente e si vuole considerarli come la stessa classe `no` di finestra. Si noti che si applicano le regole consuete sulla registrazione della classe finestra. Solo il primo componente che registra la classe finestra sarà in grado di registrarla, perché non ha una versione applicata.|

## <a name="hash"></a>hash
 `hash`L'elemento è un elemento figlio facoltativo dell'elemento `file` . L'elemento `hash` non ha attributi.

 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] usa un hash algoritmico di tutti i file in un'applicazione come controllo di sicurezza, per garantire che nessuno dei file sia stato modificato dopo la distribuzione. Se `hash` l'elemento non è incluso, questo controllo non verrà eseguito. Pertanto, l'omissione `hash` dell'elemento non è consigliata.

 Se un manifesto contiene un file di cui non è stato eseguito l'hashing, tale manifesto non può essere firmato digitalmente, perché gli utenti non possono verificare il contenuto di un file senza hash.

## <a name="dsigtransforms"></a>dsig:Transforms
 `dsig:Transforms`L'elemento è un elemento figlio obbligatorio dell'elemento `hash` . L'elemento `dsig:Transforms` non ha attributi.

## <a name="dsigtransform"></a>dsig:Transform
 `dsig:Transform`L'elemento è un elemento figlio obbligatorio dell'elemento `dsig:Transforms` . L'elemento `dsig:Transform` presenta gli attributi seguenti.

| Attributo | Descrizione |
|-------------| - |
| `Algorithm` | Algoritmo utilizzato per calcolare il digest per questo file. Attualmente l'unico valore usato da [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] è `urn:schemas-microsoft-com:HashTransforms.Identity` . |

## <a name="dsigdigestmethod"></a>dsig:DigestMethod
 `dsig:DigestMethod`L'elemento è un elemento figlio obbligatorio dell'elemento `hash` . L'elemento `dsig:DigestMethod` presenta gli attributi seguenti.

| Attributo | Descrizione |
|-------------| - |
| `Algorithm` | Algoritmo utilizzato per calcolare il digest per questo file. Attualmente l'unico valore usato da [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] è `http://www.w3.org/2000/09/xmldsig#sha1` . |

## <a name="dsigdigestvalue"></a>dsig:DigestValue
 `dsig:DigestValue`L'elemento è un elemento figlio obbligatorio dell'elemento `hash` . L'elemento `dsig:DigestValue` non ha attributi. Il valore di testo è l'hash calcolato per il file specificato.

## <a name="remarks"></a>Commenti
 Questo elemento identifica tutti i file non assembly che costituiscono l'applicazione e, in particolare, i valori hash per la verifica dei file. Questo elemento può includere anche Component Object Model di isolamento com (COM) associati al file. Se un file viene modificato, è necessario aggiornare anche il file manifesto dell'applicazione per riflettere la modifica.

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

## <a name="see-also"></a>Vedi anche
- [ClickOnce manifesto dell'applicazione](../deployment/clickonce-application-manifest.md)
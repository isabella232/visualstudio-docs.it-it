---
title: '&lt;Elemento dependency &gt; (ClickOnce Application) | Microsoft Docs'
description: L'elemento di dipendenza identifica una dipendenza di piattaforma o assembly necessaria per l'applicazione.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- urn:schemas-microsoft-com:asm.v2#osVersionInfo
- urn:schemas-microsoft-com:asm.v2#os
- http://www.w3.org/2000/09/xmldsig#Transform
- urn:schemas-microsoft-com:asm.v2#dependency
- http://www.w3.org/2000/09/xmldsig#DigestValue
- urn:schemas-microsoft-com:asm.v2#assemblyIdentity
- http://www.w3.org/2000/09/xmldsig#DigestMethod
- http://www.w3.org/2000/09/xmldsig#Transforms
- urn:schemas-microsoft-com:asm.v2#hash
- urn:schemas-microsoft-com:asm.v2#dependentAssembly
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- manifests [ClickOnce], dependency element
- <dependency> element [ClickOnce application manifest]
ms.assetid: 09d6a1e0-60f8-4fbd-843b-8e49ee3115a3
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-deployment
ms.workload:
- multiple
ms.openlocfilehash: 6dc3d0ad29597e801f4f28cc2b80335cab7240b1
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122160881"
---
# <a name="ltdependencygt-element-clickonce-application"></a>&lt;elemento dependency &gt; (ClickOnce)
Identifica una dipendenza di piattaforma o assembly necessaria per l'applicazione.

## <a name="syntax"></a>Sintassi

```xml

      <dependency>
   <dependentOS
      supportURL
      description
   >
      <osVersionInfo>
         <os
            majorVersion
            minorVersion
            buildNumber
            servicePackMajor
            servicePackMinor
            productType
            suiteType
         />
      </osVersionInfo>
   </dependentOS>
   <dependentAssembly
      dependencyType
      allowDelayedBinding
      group
      codeBase
      size
   >
      <assemblyIdentity
         name
         version
         processorArchitecture
         language
      >
         <hash>
            <dsig:Transforms>
               <dsig:Transform
                  Algorithm
            />
            </dsig:Transforms>
            <dsig:DigestMethod />
            <dsig:DigestValue>
            </dsig:DigestValue>
    </hash>

      </assemblyIdentity>
   </dependentAssembly>
</dependency>
```

## <a name="elements-and-attributes"></a>Elementi e attributi
 `dependency`L'elemento è obbligatorio. Possono essere presenti più istanze di `dependency` nello stesso manifesto dell'applicazione.

 `dependency`L'elemento non ha attributi e contiene gli elementi figlio seguenti.

### <a name="dependentos"></a>dependentOS
 facoltativo. Contiene `osVersionInfo` l'elemento . Gli `dependentOS` elementi e si `dependentAssembly` escludono a vicenda: l'uno o l'altro deve esistere per un `dependency` elemento, ma non entrambi.

 `dependentOS` supporta gli attributi seguenti.

|Attributo|Descrizione|
|---------------|-----------------|
|`supportUrl`|Facoltativa. Specifica un URL di supporto per la piattaforma dipendente. Questo URL viene visualizzato all'utente se viene trovata la piattaforma richiesta.|
|`description`|facoltativo. Descrive, in formato leggibile, il sistema operativo descritto `dependentOS` dall'elemento .|

### <a name="osversioninfo"></a>osVersionInfo
 Obbligatorio. Questo elemento è figlio dell'elemento `dependentOS` e contiene l'elemento `os` . Questo elemento non ha attributi.

### <a name="os"></a>os
 Obbligatorio. Questo elemento è figlio dell'elemento `osVersionInfo` . Questo elemento ha gli attributi seguenti.

|Attributo|Descrizione|
|---------------|-----------------|
|`majorVersion`|Obbligatorio. Specifica il numero di versione principale del sistema operativo.|
|`minorVersion`|Obbligatorio. Specifica il numero di versione secondaria del sistema operativo.|
|`buildNumber`|Obbligatorio. Specifica il numero di build del sistema operativo.|
|`servicePackMajor`|Obbligatorio. Specifica il numero principale del Service Pack del sistema operativo.|
|`servicePackMinor`|facoltativo. Specifica il numero secondario del Service Pack del sistema operativo.|
|`productType`|facoltativo. Identifica il valore del tipo di prodotto. I valori validi sono `server`, `workstation` e `domainController`. Ad esempio, per Windows 2000 Professional, questo valore di attributo è `workstation` .|
|`suiteType`|facoltativo. Identifica una suite di prodotti disponibile nel sistema o il tipo di configurazione del sistema. I valori validi sono `backoffice`, `blade`, `datacenter`, `enterprise`, `home`, `professional`, `smallbusiness`, `smallbusinessRestricted` e `terminal`. Ad esempio, per Windows 2000 Professional, questo valore di attributo è `professional` .|

### <a name="dependentassembly"></a>dependentAssembly
 facoltativo. Contiene `assemblyIdentity` l'elemento . Gli `dependentOS` elementi e si `dependentAssembly` escludono a vicenda: l'uno o l'altro deve esistere per un `dependency` elemento, ma non entrambi.

 `dependentAssembly` ha gli attributi seguenti.

| Attributo | Descrizione |
|-----------------------| - |
| `dependencyType` | Obbligatorio. Specifica il tipo di dipendenza. I valori validi sono `preprequisite` e `install`. Un `install` assembly viene installato come parte dell'applicazione. [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Un `prerequisite` assembly deve essere presente nella Global Assembly Cache (GAC) prima di poter installare [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] l'applicazione. |
| `allowDelayedBinding` | Obbligatorio. Specifica se l'assembly può essere caricato a livello di codice in fase di esecuzione. |
| `group` | facoltativo. Se `dependencyType` l'attributo è impostato su `install` , definisce un gruppo denominato di assembly che vengono installati solo su richiesta. Per altre informazioni, vedere [Procedura dettagliata: Download di assembly su richiesta con l'API della distribuzione ClickOnce tramite la finestra di progettazione](../deployment/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer.md).<br /><br /> Se impostato su `framework` e `dependencyType` l'attributo è impostato su `prerequisite` , designa l'assembly come parte del .NET Framework. La Global Assembly Cache (GAC) non viene verificata per questo assembly durante l'installazione in .NET Framework 4 e versioni successive. |
| `codeBase` | Obbligatorio quando `dependencyType` l'attributo è impostato su `install` . Percorso dell'assembly dipendente. Può essere un percorso assoluto o un percorso relativo alla codebase del manifesto. Questo percorso deve essere un URI valido perché il manifesto dell'assembly sia valido. |
| `size` | Obbligatorio quando `dependencyType` l'attributo è impostato su `install` . Dimensioni dell'assembly dipendente, in byte. |

### <a name="assemblyidentity"></a>assemblyIdentity
 Obbligatorio. Questo elemento è figlio dell'elemento `dependentAssembly` e ha l'attributo seguente.

|Attributo|Descrizione|
|---------------|-----------------|
|`name`|Obbligatorio. Identifica il nome dell'applicazione.|
|`version`|Obbligatorio. Specifica il numero di versione dell'applicazione nel formato seguente: `major.minor.build.revision`|
|`publicKeyToken`|facoltativo. Specifica una stringa esadecimale di 16 caratteri che rappresenta gli ultimi 8 byte del valore hash della chiave pubblica con cui viene firmata l'applicazione o `SHA-1` l'assembly. La chiave pubblica usata per firmare il catalogo deve essere di 2048 bit o superiore.|
|`processorArchitecture`|facoltativo. Specifica il processore. I valori validi sono per le Windows a 32 bit e per le Windows `x86` `I64` a 64 bit.|
|`language`|facoltativo. Identifica i codici lingua in due parti, ad esempio EN-US, dell'assembly.|

### <a name="hash"></a>hash
 `hash`L'elemento è un elemento figlio facoltativo dell'elemento `assemblyIdentity` . L'elemento `hash` non ha attributi.

 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] usa un hash algoritmico di tutti i file in un'applicazione come controllo di sicurezza, per garantire che nessuno dei file sia stato modificato dopo la distribuzione. Se `hash` l'elemento non è incluso, questo controllo non verrà eseguito. Pertanto, l'omissione `hash` dell'elemento non è consigliata.

### <a name="dsigtransforms"></a>dsig:Transforms
 `dsig:Transforms`L'elemento è un elemento figlio obbligatorio dell'elemento `hash` . L'elemento `dsig:Transforms` non ha attributi.

### <a name="dsigtransform"></a>dsig:Transform
 `dsig:Transform`L'elemento è un elemento figlio obbligatorio dell'elemento `dsig:Transforms` . L'elemento `dsig:Transform` presenta gli attributi seguenti.

| Attributo | Descrizione |
|-------------| - |
| `Algorithm` | Algoritmo utilizzato per calcolare il digest per questo file. Attualmente l'unico valore usato da [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] è `urn:schemas-microsoft-com:HashTransforms.Identity` . |

### <a name="dsigdigestmethod"></a>dsig:DigestMethod
 `dsig:DigestMethod`L'elemento è un elemento figlio obbligatorio dell'elemento `hash` . L'elemento `dsig:DigestMethod` presenta gli attributi seguenti.

| Attributo | Descrizione |
|-------------| - |
| `Algorithm` | Algoritmo utilizzato per calcolare il digest per questo file. Attualmente l'unico valore usato da [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] è `http://www.w3.org/2000/09/xmldsig#sha1` . |

### <a name="dsigdigestvalue"></a>dsig:DigestValue
 `dsig:DigestValue`L'elemento è un elemento figlio obbligatorio dell'elemento `hash` . L'elemento `dsig:DigestValue` non ha attributi. Il valore di testo è l'hash calcolato per il file specificato.

## <a name="remarks"></a>Commenti
 Tutti gli assembly usati dall'applicazione devono avere un elemento `dependency` corrispondente. Gli assembly dipendenti non includono gli assembly che devono essere preinstallati nella Global Assembly Cache come assembly della piattaforma.

## <a name="example"></a>Esempio
 L'esempio di codice seguente illustra gli `dependency` elementi in un manifesto [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] dell'applicazione. Questo esempio di codice fa parte di un esempio più ampio fornito per [l'ClickOnce manifesto dell'applicazione.](../deployment/clickonce-application-manifest.md)

```xml
<dependency>
  <dependentOS>
    <osVersionInfo>
      <os
        majorVersion="4"
        minorVersion="10"
        buildNumber="0"
        servicePackMajor="0" />
    </osVersionInfo>
  </dependentOS>
</dependency>
<dependency>
  <dependentAssembly
    dependencyType="preRequisite"
    allowDelayedBinding="true">
    <assemblyIdentity
      name="Microsoft.Windows.CommonLanguageRuntime"
      version="4.0.20506.0" />
  </dependentAssembly>
</dependency>

<dependency>
  <dependentAssembly
    dependencyType="install"
    allowDelayedBinding="true"
    codebase="MyApplication.exe"
    size="4096">
    <assemblyIdentity
      name="MyApplication"
      version="1.0.0.0"
      language="neutral"
      processorArchitecture="x86" />
    <hash>
      <dsig:Transforms>
        <dsig:Transform Algorithm="urn:schemas-microsoft-com:HashTransforms.Identity" />
      </dsig:Transforms>
      <dsig:DigestMethod Algorithm="http://www.w3.org/2000/09/xmldsig#sha1" />
      <dsig:DigestValue>DpTW7RzS9IeT/RBSLj54vfTEzNg=</dsig:DigestValue>
    </hash>
  </dependentAssembly>
</dependency>
```

## <a name="see-also"></a>Vedi anche
- [ClickOnce manifesto dell'applicazione](../deployment/clickonce-application-manifest.md)
- [\<dependency> Elemento](../deployment/dependency-element-clickonce-deployment.md)
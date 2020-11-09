---
title: '&lt;&gt;elemento dependency (applicazione ClickOnce) | Microsoft Docs'
description: L'elemento dependency identifica una dipendenza della piattaforma o dell'assembly necessaria per l'applicazione.
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e7896fa2d39bafc793c5fd74f66f4991cf5e8461
ms.sourcegitcommit: 0893244403aae9187c9375ecf0e5c221c32c225b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/09/2020
ms.locfileid: "94382949"
---
# <a name="ltdependencygt-element-clickonce-application"></a>&lt;&gt;elemento dependency (applicazione ClickOnce)
Identifica una dipendenza della piattaforma o dell'assembly necessaria per l'applicazione.

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
 L' `dependency` elemento è obbligatorio. Nello stesso manifesto dell'applicazione possono essere presenti più istanze di `dependency` .

 L' `dependency` elemento non ha attributi e contiene gli elementi figlio seguenti.

### <a name="dependentos"></a>dependentOS
 Facoltativa. Contiene l' `osVersionInfo` elemento. Gli `dependentOS` elementi e si escludono a vicenda `dependentAssembly` : uno o l'altro deve esistere per un `dependency` elemento, ma non entrambi.

 `dependentOS` supporta i seguenti attributi.

|Attributo|Descrizione|
|---------------|-----------------|
|`supportUrl`|Facoltativa. Specifica un URL di supporto per la piattaforma dipendente. Questo URL viene visualizzato all'utente se viene trovata la piattaforma richiesta.|
|`description`|Facoltativa. Descrive, nel formato leggibile, il sistema operativo descritto dall' `dependentOS` elemento.|

### <a name="osversioninfo"></a>osVersionInfo
 Obbligatorio. Questo elemento è figlio dell'elemento `dependentOS` e contiene l'elemento `os` . Questo elemento non ha attributi.

### <a name="os"></a>os
 Obbligatorio. Questo elemento è figlio dell'elemento `osVersionInfo` . Questo elemento ha gli attributi seguenti.

|Attributo|Descrizione|
|---------------|-----------------|
|`majorVersion`|Obbligatorio. Specifica il numero di versione principale del sistema operativo.|
|`minorVersion`|Obbligatorio. Specifica il numero della versione secondaria del sistema operativo.|
|`buildNumber`|Obbligatorio. Specifica il numero di build del sistema operativo.|
|`servicePackMajor`|Obbligatorio. Specifica il Service Pack numero principale del sistema operativo.|
|`servicePackMinor`|Facoltativa. Specifica il Service Pack numero secondario del sistema operativo.|
|`productType`|Facoltativa. Identifica il valore del tipo di prodotto. I valori validi sono `server`, `workstation` e `domainController`. Ad esempio, per Windows 2000 Professional, questo valore dell'attributo è `workstation` .|
|`suiteType`|Facoltativa. Identifica una suite di prodotti disponibile nel sistema o il tipo di configurazione del sistema. I valori validi sono `backoffice`, `blade`, `datacenter`, `enterprise`, `home`, `professional`, `smallbusiness`, `smallbusinessRestricted` e `terminal`. Ad esempio, per Windows 2000 Professional, questo valore dell'attributo è `professional` .|

### <a name="dependentassembly"></a>dependentAssembly
 Facoltativa. Contiene l' `assemblyIdentity` elemento. Gli `dependentOS` elementi e si escludono a vicenda `dependentAssembly` : uno o l'altro deve esistere per un `dependency` elemento, ma non entrambi.

 `dependentAssembly` ha gli attributi seguenti.

| Attributo | Descrizione |
|-----------------------| - |
| `dependencyType` | Obbligatorio. Specifica il tipo di dipendenza. I valori validi sono `preprequisite` e `install`. Un `install` assembly viene installato come parte dell' [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] applicazione. `prerequisite`Prima di poter installare l'applicazione, è necessario che nell'global assembly cache (GAC) sia presente un assembly [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] . |
| `allowDelayedBinding` | Obbligatorio. Specifica se l'assembly può essere caricato a livello di codice in fase di esecuzione. |
| `group` | Facoltativa. Se l' `dependencyType` attributo è impostato su `install` , definisce un gruppo di assembly denominato che viene installato solo su richiesta. Per altre informazioni, vedere [Procedura dettagliata: Download di assembly su richiesta con l'API della distribuzione ClickOnce tramite la finestra di progettazione](../deployment/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer.md).<br /><br /> Se è impostato su `framework` e l' `dependencyType` attributo è impostato su `prerequisite` , definisce l'assembly come parte del .NET Framework. La cache assemby globale (GAC) non viene verificata per l'assembly quando si esegue l'installazione in .NET Framework 4 e versioni successive. |
| `codeBase` | Obbligatorio quando l' `dependencyType` attributo è impostato su `install` . Percorso dell'assembly dipendente. Può essere un percorso assoluto o un percorso relativo alla codebase del manifesto. Questo percorso deve essere un URI valido affinché il manifesto dell'assembly sia valido. |
| `size` | Obbligatorio quando l' `dependencyType` attributo è impostato su `install` . Dimensioni in byte dell'assembly dipendente. |

### <a name="assemblyidentity"></a>assemblyIdentity
 Obbligatorio. Questo elemento è figlio dell'elemento `dependentAssembly` e ha l'attributo seguente.

|Attributo|Descrizione|
|---------------|-----------------|
|`name`|Obbligatorio. Identifica il nome dell'applicazione.|
|`version`|Obbligatorio. Specifica il numero di versione dell'applicazione nel formato seguente: `major.minor.build.revision`|
|`publicKeyToken`|Facoltativa. Specifica una stringa esadecimale di 16 caratteri che rappresenta gli ultimi 8 byte del `SHA-1` valore hash della chiave pubblica in cui l'applicazione o l'assembly è firmato. La chiave pubblica usata per firmare il catalogo deve essere di 2048 bit o superiore.|
|`processorArchitecture`|Facoltativa. Specifica il processore. I valori validi sono `x86` per Windows a 32 bit e `I64` per windows a 64 bit.|
|`language`|Facoltativa. Identifica i codici di lingua in due parti, ad esempio EN-US, dell'assembly.|

### <a name="hash"></a>hash
 L' `hash` elemento è un elemento figlio facoltativo dell' `assemblyIdentity` elemento. L'elemento `hash` non ha attributi.

 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Usa un hash algoritmico di tutti i file di un'applicazione come controllo di sicurezza, per garantire che nessuno dei file sia stato modificato dopo la distribuzione. Se l' `hash` elemento non è incluso, questo controllo non verrà eseguito. Non è pertanto consigliabile omettere l' `hash` elemento.

### <a name="dsigtransforms"></a>dsig:Transforms
 L' `dsig:Transforms` elemento è un figlio obbligatorio dell' `hash` elemento. L'elemento `dsig:Transforms` non ha attributi.

### <a name="dsigtransform"></a>dsig:Transform
 L' `dsig:Transform` elemento è un figlio obbligatorio dell' `dsig:Transforms` elemento. L'elemento `dsig:Transform` presenta gli attributi seguenti.

| Attributo | Descrizione |
|-------------| - |
| `Algorithm` | Algoritmo utilizzato per calcolare il digest per il file. Attualmente l'unico valore utilizzato da [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] è `urn:schemas-microsoft-com:HashTransforms.Identity` . |

### <a name="dsigdigestmethod"></a>dsig: DigestMethod
 L' `dsig:DigestMethod` elemento è un figlio obbligatorio dell' `hash` elemento. L'elemento `dsig:DigestMethod` presenta gli attributi seguenti.

| Attributo | Descrizione |
|-------------| - |
| `Algorithm` | Algoritmo utilizzato per calcolare il digest per il file. Attualmente l'unico valore utilizzato da [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] è `http://www.w3.org/2000/09/xmldsig#sha1` . |

### <a name="dsigdigestvalue"></a>dsig: DigestValue
 L' `dsig:DigestValue` elemento è un figlio obbligatorio dell' `hash` elemento. L'elemento `dsig:DigestValue` non ha attributi. Il valore di testo è l'hash calcolato per il file specificato.

## <a name="remarks"></a>Commenti
 Tutti gli assembly usati dall'applicazione devono avere un `dependency` elemento corrispondente. Gli assembly dipendenti non includono assembly che devono essere preinstallati nel Global Assembly Cache come assembly della piattaforma.

## <a name="example"></a>Esempio
 Nell'esempio di codice seguente vengono illustrati `dependency` gli elementi in un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifesto dell'applicazione. Questo esempio di codice fa parte di un esempio più ampio fornito per l'argomento [manifesto dell'applicazione ClickOnce](../deployment/clickonce-application-manifest.md) .

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

## <a name="see-also"></a>Vedere anche
- [Manifesto dell'applicazione ClickOnce](../deployment/clickonce-application-manifest.md)
- [\<dependency> elemento](../deployment/dependency-element-clickonce-deployment.md)
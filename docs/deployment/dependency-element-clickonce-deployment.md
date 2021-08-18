---
title: '&lt;Elemento dependency &gt; (ClickOnce Deployment) | Microsoft Docs'
description: L'elemento di dipendenza identifica la versione dell'applicazione da installare e il percorso del manifesto dell'applicazione.
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
- <dependency> element [ClickOnce deployment manifest]
ms.assetid: 9b4d2082-0347-4922-ac70-85f11b913039
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-deployment
ms.workload:
- multiple
ms.openlocfilehash: 27da36d933a3505163c36623b9eac8b51d0bbe86
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122160868"
---
# <a name="ltdependencygt-element-clickonce-deployment"></a>&lt;elemento dependency &gt; (distribuzione ClickOnce)
Identifica la versione dell'applicazione da installare e il percorso del manifesto dell'applicazione.

## <a name="syntax"></a>Sintassi

```xml

      <dependency>
   <dependentAssembly
      preRequisite
      visible
      dependencyType
      codeBase
      size
   >
      <assemblyIdentity
         name
         version
         publicKeyToken
         processorArchitecture
         language
         type
      />
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

   </dependentAssembly>
</dependency>
```

## <a name="elements-and-attributes"></a>Elementi e attributi
 `dependency`L'elemento è obbligatorio. Non dispone di attributi. Un manifesto della distribuzione può avere più `dependency` elementi.

 `dependency`L'elemento in genere esprime le dipendenze per l'applicazione principale negli assembly contenuti in un'applicazione. [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Se lMain.exe applizione usa un assembly denominato DotNetAssembly.dll, tale assembly deve essere elencato in una sezione di dipendenza. La dipendenza, tuttavia, può esprimere anche altri tipi di dipendenze, ad esempio dipendenze da una versione specifica di Common Language Runtime, da un assembly nella Global Assembly Cache (GAC) o da un oggetto COM. Poiché si tratta di una tecnologia di distribuzione senza tocco, non può avviare il download e l'installazione di questi tipi di dipendenze, ma impedisce l'esecuzione dell'applicazione se una o più delle dipendenze specificate non [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] esistono.

## <a name="dependentassembly"></a>dependentAssembly
 Obbligatorio. Questo elemento contiene `assemblyIdentity` l'elemento . Nella tabella seguente vengono illustrati gli attributi `dependentAssembly` supportati da .

| Attributo | Descrizione |
|------------------| - |
| `preRequisite` | Facoltativa. Specifica che l'assembly deve essere già presente nella GAC. I valori validi sono `true` e `false`. Se `true` e l'assembly specificato non esiste nella GAC, l'esecuzione dell'applicazione non riesce. |
| `visible` | facoltativo. Identifica l'identità dell'applicazione di primo livello, incluse le relative dipendenze. Usato internamente da per [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] gestire l'archiviazione e l'attivazione delle applicazioni. |
| `dependencyType` | Obbligatorio. Relazione tra questa dipendenza e l'applicazione. I valori validi sono:<br /><br /> -   `install`. Il componente rappresenta un'installazione separata dall'applicazione corrente.<br />-   `preRequisite`. Il componente è richiesto dall'applicazione corrente. |
| `codebase` | facoltativo. Percorso completo del manifesto dell'applicazione. |
| `size` | facoltativo. Dimensioni del manifesto dell'applicazione, in byte. |

## <a name="assemblyidentity"></a>assemblyIdentity
 Obbligatorio. Questo elemento è figlio dell'elemento `dependentAssembly` . Il contenuto di `assemblyIdentity` deve essere identico a quello descritto nel manifesto [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] dell'applicazione. Nella tabella seguente vengono illustrati gli attributi `assemblyIdentity` dell'elemento .

|Attributo|Descrizione|
|---------------|-----------------|
|`Name`|Obbligatorio. Identifica il nome dell'applicazione.|
|`Version`|Obbligatorio. Specifica il numero di versione dell'applicazione, nel formato seguente: `major.minor.build.revision`|
|`publicKeyToken`|Obbligatorio. Specifica una stringa esadecimale di 16 caratteri che rappresenta gli ultimi 8 byte dell'hash SHA-1 della chiave pubblica con cui viene firmata l'applicazione o l'assembly. La chiave pubblica usata per firmare deve essere a 2048 bit o superiore.|
|`processorArchitecture`|Obbligatorio. Specifica il microprocessore. I valori validi sono per le Windows a 32 bit e per le Windows `x86` `IA64` a 64 bit.|
|`Language`|facoltativo. Identifica i codici lingua in due parti dell'assembly. Ad esempio, EN-US, che sta per Inglese (Stati Uniti). Il valore predefinito è `neutral`. Questo elemento si trova nello spazio `asmv2` dei nomi .|
|`type`|facoltativo. Per la compatibilità con le versioni Windows tecnologia di installazione side-by-side. L'unico valore consentito è `win32` .|

## <a name="hash"></a>hash
 `hash`L'elemento è un elemento figlio facoltativo dell'elemento `file` . L'elemento `hash` non ha attributi.

 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] usa un hash algoritmico di tutti i file in un'applicazione come controllo di sicurezza per garantire che nessuno dei file sia stato modificato dopo la distribuzione. Se `hash` l'elemento non è incluso, questo controllo non verrà eseguito. Pertanto, l'omissione `hash` dell'elemento non è consigliata.

## <a name="dsigtransforms"></a>dsig:Transforms
 `dsig:Transforms`L'elemento è un elemento figlio obbligatorio dell'elemento `hash` . L'elemento `dsig:Transforms` non ha attributi.

## <a name="dsigtransform"></a>dsig:Transform
 `dsig:Transform`L'elemento è un elemento figlio obbligatorio dell'elemento `dsig:Transforms` . Nella tabella seguente vengono illustrati gli attributi `dsig:Transform` dell'elemento .

| Attributo | Descrizione |
|-------------| - |
| `Algorithm` | Algoritmo utilizzato per calcolare il digest per questo file. Attualmente l'unico valore usato da [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] è `urn:schemas-microsoft-com:HashTransforms.Identity` . |

## <a name="dsigdigestmethod"></a>dsig:DigestMethod
 `dsig:DigestMethod`L'elemento è un elemento figlio obbligatorio dell'elemento `hash` . Nella tabella seguente vengono illustrati gli attributi `dsig:DigestMethod` dell'elemento .

| Attributo | Descrizione |
|-------------| - |
| `Algorithm` | Algoritmo utilizzato per calcolare il digest per questo file. Attualmente l'unico valore usato da [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] è `http://www.w3.org/2000/09/xmldsig#sha1` . |

## <a name="dsigdigestvalue"></a>dsig:DigestValue
 `dsig:DigestValue`L'elemento è un elemento figlio obbligatorio dell'elemento `hash` . L'elemento `dsig:DigestValue` non ha attributi. Il valore di testo è l'hash calcolato per il file specificato.

## <a name="remarks"></a>Commenti
 I manifesti di distribuzione hanno in genere un `assemblyIdentity` singolo elemento che identifica il nome e la versione del manifesto dell'applicazione.

## <a name="example-1"></a>Esempio 1
 Nell'esempio di codice seguente viene illustrato `dependency` un elemento in un manifesto della [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] distribuzione.

```xml
<!-- Identify the assembly dependencies -->
<dependency>
  <dependentAssembly dependencyType="install" allowDelayedBinding="true" codebase="MyApplication.exe" size="16384">
    <assemblyIdentity name="MyApplication" version="0.0.0.0" cultural="neutral" processorArchitecture="msil" />
    <hash>
      <dsig:Transforms>
        <dsig:Transform Algorithm="urn:schemas-microsoft-com:HashTransforms.Identity" />
      </dsig:Transforms>
      <dsig:DigestMethod Algorithm="http://www.w3.org/2000/09/xmldsig#sha1" />
       <dsig:DigestValue>YzXYZJAvj9pgAG3y8jXUjC7AtHg=</dsig:DigestValue>
    </hash>
  </dependentAssembly>
</dependency>
```

## <a name="example-2"></a>Esempio 2
 Nell'esempio di codice seguente viene specificata una dipendenza da un assembly già installato nella GAC.

```xml
<dependency>
  <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true">
    <assemblyIdentity name="GACAssembly" version="1.0.0.0" language="neutral" processorArchitecture="msil" />
  </dependentAssembly>
</dependency>
```

## <a name="example-3"></a>Esempio 3
 Nell'esempio di codice seguente viene specificata una dipendenza da una versione specifica di Common Language Runtime.

```xml
<dependency>
  <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true">
    <assemblyIdentity name="Microsoft.Windows.CommonLanguageRuntime" version="2.0.50215.0" />
  </dependentAssembly>
</dependency>
```

## <a name="example-4"></a>Esempio 4
 Nell'esempio di codice seguente viene specificata una dipendenza del sistema operativo.

```xml
<dependency>
   <dependentOS supportUrl="http://www.microsoft.com" description="Microsoft Windows Operating System">
      <osVersionInfo>
         <os majorVersion="4" minorVersion="10" />
      </osVersionInfo>
   </dependentOS>
</dependency>
```

## <a name="see-also"></a>Vedi anche
- [ClickOnce di distribuzione](../deployment/clickonce-deployment-manifest.md)
- [\<dependency> Elemento](../deployment/dependency-element-clickonce-application.md)
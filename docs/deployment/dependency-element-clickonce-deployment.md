---
title: '&lt;&gt;elemento dependency (distribuzione ClickOnce) | Microsoft Docs'
description: L'elemento dependency identifica la versione dell'applicazione da installare e il percorso del manifesto dell'applicazione.
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
ms.workload:
- multiple
ms.openlocfilehash: 172f3ea546565554c5f0701b81a88b9ca99b4100
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99881100"
---
# <a name="ltdependencygt-element-clickonce-deployment"></a>&lt;&gt;elemento dependency (distribuzione ClickOnce)
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
 L' `dependency` elemento è obbligatorio. Non ha attributi. Un manifesto di distribuzione può avere più `dependency` elementi.

 L' `dependency` elemento in genere esprime le dipendenze per l'applicazione principale negli assembly contenuti in un' [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] applicazione. Se l'applicazione Main.exe utilizza un assembly denominato DotNetAssembly.dll, tale assembly deve essere elencato in una sezione di dipendenza. La dipendenza, tuttavia, può anche esprimere altri tipi di dipendenze, ad esempio dipendenze da una versione specifica del Common Language Runtime, in un assembly nella Global Assembly Cache (GAC) o in un oggetto COM. Poiché si tratta di una tecnologia di distribuzione senza tocco, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] non è in grado di avviare il download e l'installazione di questi tipi di dipendenze, ma impedisce l'esecuzione dell'applicazione se una o più dipendenze specificate non esistono.

## <a name="dependentassembly"></a>dependentAssembly
 Obbligatorio. Questo elemento contiene l' `assemblyIdentity` elemento. La tabella seguente illustra gli attributi `dependentAssembly` supportati da.

| Attributo | Descrizione |
|------------------| - |
| `preRequisite` | Facoltativa. Specifica che l'assembly deve essere già presente nella GAC. I valori validi sono `true` e `false`. Se `true` e l'assembly specificato non esiste nella GAC, l'esecuzione dell'applicazione non riesce. |
| `visible` | facoltativo. Identifica l'identità dell'applicazione di primo livello, incluse le relative dipendenze. Utilizzato internamente da [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] per gestire l'attivazione e l'archiviazione dell'applicazione. |
| `dependencyType` | Obbligatorio. Relazione tra la dipendenza e l'applicazione. I valori validi sono:<br /><br /> -   `install`. Il componente rappresenta un'installazione separata dall'applicazione corrente.<br />-   `preRequisite`. Il componente è necessario per l'applicazione corrente. |
| `codebase` | facoltativo. Percorso completo del manifesto dell'applicazione. |
| `size` | facoltativo. Dimensioni in byte del manifesto dell'applicazione. |

## <a name="assemblyidentity"></a>assemblyIdentity
 Obbligatorio. Questo elemento è figlio dell'elemento `dependentAssembly` . Il contenuto di `assemblyIdentity` deve essere uguale a quello descritto nel [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifesto dell'applicazione. La tabella seguente illustra gli attributi dell' `assemblyIdentity` elemento.

|Attributo|Descrizione|
|---------------|-----------------|
|`Name`|Obbligatorio. Identifica il nome dell'applicazione.|
|`Version`|Obbligatorio. Specifica il numero di versione dell'applicazione, nel formato seguente: `major.minor.build.revision`|
|`publicKeyToken`|Obbligatorio. Specifica una stringa esadecimale di 16 caratteri che rappresenta gli ultimi 8 byte dell'hash SHA-1 della chiave pubblica in cui l'applicazione o l'assembly è firmato. La chiave pubblica usata per firmare deve avere una lunghezza massima di 2048 bit.|
|`processorArchitecture`|Obbligatorio. Specifica il microprocessore. I valori validi sono `x86` per Windows a 32 bit e `IA64` per windows a 64 bit.|
|`Language`|facoltativo. Identifica i codici di lingua in due parti dell'assembly. Ad esempio, EN-US, che sta per la lingua inglese (Stati Uniti). Il valore predefinito è `neutral`. Questo elemento si trova nello `asmv2` spazio dei nomi.|
|`type`|facoltativo. Per la compatibilità con le versioni precedenti con la tecnologia di installazione side-by-side di Windows. L'unico valore consentito è `win32` .|

## <a name="hash"></a>hash
 L' `hash` elemento è un elemento figlio facoltativo dell' `file` elemento. L'elemento `hash` non ha attributi.

 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Usa un hash algoritmico di tutti i file di un'applicazione come controllo di sicurezza per garantire che nessuno dei file sia stato modificato dopo la distribuzione. Se l' `hash` elemento non è incluso, questo controllo non verrà eseguito. Non è pertanto consigliabile omettere l' `hash` elemento.

## <a name="dsigtransforms"></a>dsig:Transforms
 L' `dsig:Transforms` elemento è un figlio obbligatorio dell' `hash` elemento. L'elemento `dsig:Transforms` non ha attributi.

## <a name="dsigtransform"></a>dsig:Transform
 L' `dsig:Transform` elemento è un figlio obbligatorio dell' `dsig:Transforms` elemento. La tabella seguente illustra gli attributi dell' `dsig:Transform` elemento.

| Attributo | Descrizione |
|-------------| - |
| `Algorithm` | Algoritmo utilizzato per calcolare il digest per il file. Attualmente l'unico valore utilizzato da [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] è `urn:schemas-microsoft-com:HashTransforms.Identity` . |

## <a name="dsigdigestmethod"></a>dsig: DigestMethod
 L' `dsig:DigestMethod` elemento è un figlio obbligatorio dell' `hash` elemento. La tabella seguente illustra gli attributi dell' `dsig:DigestMethod` elemento.

| Attributo | Descrizione |
|-------------| - |
| `Algorithm` | Algoritmo utilizzato per calcolare il digest per il file. Attualmente l'unico valore utilizzato da [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] è `http://www.w3.org/2000/09/xmldsig#sha1` . |

## <a name="dsigdigestvalue"></a>dsig: DigestValue
 L' `dsig:DigestValue` elemento è un figlio obbligatorio dell' `hash` elemento. L'elemento `dsig:DigestValue` non ha attributi. Il valore di testo è l'hash calcolato per il file specificato.

## <a name="remarks"></a>Commenti
 I manifesti della distribuzione hanno in genere un singolo `assemblyIdentity` elemento che identifica il nome e la versione del manifesto dell'applicazione.

## <a name="example-1"></a>Esempio 1
 Nell'esempio di codice riportato di seguito viene illustrato un `dependency` elemento in un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifesto di distribuzione.

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
 Nell'esempio di codice seguente viene specificata una dipendenza da una versione specifica del Common Language Runtime.

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
- [Manifesto della distribuzione ClickOnce](../deployment/clickonce-deployment-manifest.md)
- [\<dependency> elemento](../deployment/dependency-element-clickonce-application.md)
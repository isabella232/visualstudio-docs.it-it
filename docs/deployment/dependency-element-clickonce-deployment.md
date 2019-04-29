---
title: '&lt;dipendenza&gt; elemento (distribuzione ClickOnce) | Microsoft Docs'
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 84e26a2d7dae70e0029817d4e6bb6e70dd53bce4
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62928945"
---
# <a name="ltdependencygt-element-clickonce-deployment"></a>&lt;dipendenza&gt; elemento (distribuzione ClickOnce)
Identifica la versione dell'applicazione per l'installazione e la posizione del manifesto dell'applicazione.

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
 Il `dependency` elemento è obbligatorio. Non dispone di attributi. Un manifesto di distribuzione può avere più `dependency` elementi.

 Il `dependency` elemento esprime in genere le dipendenze dell'applicazione principale negli assembly contenuti all'interno di un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] dell'applicazione. Se l'applicazione Main.exe utilizza un assembly denominato DotNetAssembly. dll, tale assembly deve essere elencato nella sezione delle dipendenze. Dipendenza, tuttavia, può inoltre essere formulata altri tipi di dipendenze, ad esempio dipendenze da una versione specifica di common language runtime, in un assembly nella global assembly cache (GAC) o su un oggetto COM. Perché è una tecnologia di distribuzione automatica, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] non è possibile avviare il download e installazione di questi tipi di dipendenze, ma impedisce l'esecuzione dell'applicazione se non sono presenti uno o più dipendenze specificate.

## <a name="dependentassembly"></a>dependentAssembly
 Obbligatorio. Questo elemento contiene il `assemblyIdentity` elemento. La tabella seguente illustra gli attributi di `dependentAssembly` supporta.

| Attributo | Descrizione |
|------------------| - |
| `preRequisite` | Facoltativo. Specifica che l'assembly deve essere già esistente nella Global Assembly Cache. I valori validi sono `true` e `false`. Se `true`e l'assembly specificato non esiste nella Global Assembly Cache, non è possibile eseguire l'applicazione. |
| `visible` | Facoltativo. Identifica l'identità di applicazione di primo livello, incluse le relative dipendenze. Utilizzato internamente da [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] per gestire archiviazione di applicazioni e attivazione. |
| `dependencyType` | Obbligatorio. La relazione tra questa dipendenza e l'applicazione. I valori validi sono:<br /><br /> -   `install`. Componente rappresenta un'installazione separata dall'applicazione corrente.<br />-   `preRequisite`. Componente è necessario per l'applicazione corrente. |
| `codebase` | Facoltativo. Il percorso completo del manifesto dell'applicazione. |
| `size` | Facoltativo. Le dimensioni del manifesto dell'applicazione, in byte. |

## <a name="assemblyidentity"></a>assemblyIdentity
 Obbligatorio. Questo elemento è figlio dell'elemento `dependentAssembly` . Il contenuto del `assemblyIdentity` deve essere identico a quello descritto nel [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifesto dell'applicazione. La tabella seguente illustra gli attributi del `assemblyIdentity` elemento.

|Attributo|Descrizione|
|---------------|-----------------|
|`Name`|Obbligatorio. Identifica il nome dell'applicazione.|
|`Version`|Obbligatorio. Specifica il numero di versione dell'applicazione, nel formato seguente: `major.minor.build.revision`|
|`publicKeyToken`|Obbligatorio. Specifica una stringa esadecimale a 16 caratteri che rappresenta gli ultimi 8 byte dell'hash SHA-1 della chiave pubblica utilizzata per firmare l'applicazione o assembly. La chiave pubblica usata per firmare deve essere 2048 bit o superiore.|
|`processorArchitecture`|Obbligatorio. Specifica il microprocessore. I valori validi sono `x86` per Windows a 32 bit e `IA64` per Windows a 64 bit.|
|`Language`|Facoltativo. Identifica i codici di lingua di due parti dell'assembly. Ad esempio, EN-US, che è l'acronimo per inglese (Stati Uniti). Il valore predefinito è `neutral`. Questo elemento è presente il `asmv2` dello spazio dei nomi.|
|`type`|Facoltativo. Per tecnologia di installazione compatibilità con Windows side-by-side con le versioni precedenti. L'unico valore consentito è `win32`.|

## <a name="hash"></a>hash
 Il `hash` costituisce un elemento figlio facoltativo di `file` elemento. L'elemento `hash` non ha attributi.

 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Usa un hash algoritmico di tutti i file in un'applicazione come un controllo di sicurezza per assicurarsi che nessuno dei file sono stati modificati dopo la distribuzione. Se il `hash` elemento non è incluso, questo controllo non verrà eseguito. Pertanto, l'omissione di `hash` elemento non è consigliato.

## <a name="dsigtransforms"></a>dsig:Transforms
 Il `dsig:Transforms` elemento è un elemento figlio obbligatorio del `hash` elemento. L'elemento `dsig:Transforms` non ha attributi.

## <a name="dsigtransform"></a>dsig:Transform
 Il `dsig:Transform` elemento è un elemento figlio obbligatorio del `dsig:Transforms` elemento. La tabella seguente illustra gli attributi del `dsig:Transform` elemento.

| Attributo | Descrizione |
|-------------| - |
| `Algorithm` | L'algoritmo utilizzato per la quale calcolare il digest per questo file. Attualmente l'unico valore usato da [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] è `urn:schemas-microsoft-com:HashTransforms.Identity`. |

## <a name="dsigdigestmethod"></a>dsig: DigestMethod
 Il `dsig:DigestMethod` elemento è un elemento figlio obbligatorio del `hash` elemento. La tabella seguente illustra gli attributi del `dsig:DigestMethod` elemento.

| Attributo | Descrizione |
|-------------| - |
| `Algorithm` | L'algoritmo utilizzato per la quale calcolare il digest per questo file. Attualmente l'unico valore usato da [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] è `http://www.w3.org/2000/09/xmldsig#sha1`. |

## <a name="dsigdigestvalue"></a>dsig:
 Il `dsig:DigestValue` elemento è un elemento figlio obbligatorio del `hash` elemento. L'elemento `dsig:DigestValue` non ha attributi. Il valore di testo è l'hash calcolato per il file specificato.

## <a name="remarks"></a>Note
 Manifesti di distribuzione hanno in genere un singolo `assemblyIdentity` elemento che identifica il nome e la versione del manifesto dell'applicazione.

## <a name="example"></a>Esempio
 Nell'esempio di codice riportato di seguito viene illustrato un `dependency` elemento in un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifesto della distribuzione.

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

## <a name="example"></a>Esempio
 Esempio di codice seguente specifica una dipendenza in un assembly già installato nella Global Assembly Cache.

```xml
<dependency>
  <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true">
    <assemblyIdentity name="GACAssembly" version="1.0.0.0" language="neutral" processorArchitecture="msil" />
  </dependentAssembly>
</dependency>
```

## <a name="example"></a>Esempio
 Esempio di codice seguente specifica una dipendenza su una versione specifica di common language runtime.

```xml
<dependency>
  <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true">
    <assemblyIdentity name="Microsoft.Windows.CommonLanguageRuntime" version="2.0.50215.0" />
  </dependentAssembly>
</dependency>
```

## <a name="example"></a>Esempio
 Esempio di codice seguente specifica una dipendenza del sistema operativo.

```xml
<dependency>
   <dependentOS supportUrl="http://www.microsoft.com" description="Microsoft Windows Operating System">
      <osVersionInfo>
         <os majorVersion="4" minorVersion="10" />
      </osVersionInfo>
   </dependentOS>
</dependency>
```

## <a name="see-also"></a>Vedere anche
- [Manifesto di distribuzione ClickOnce](../deployment/clickonce-deployment-manifest.md)
- [\<dipendenza > elemento](../deployment/dependency-element-clickonce-application.md)
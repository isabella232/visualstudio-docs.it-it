---
title: Direttiva output T4
ms.date: 11/04/2016
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 624afd32a9b0f44e3190fba7e3b126663b96f6f4
ms.sourcegitcommit: ad5fb20f18b23eb8bd2568717f61edc6b7eee5e7
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47860199"
---
# <a name="t4-output-directive"></a>Direttiva output T4

Nei modelli di testo di Visual Studio, il `output` direttiva viene usata per definire l'estensione del nome file e la codifica del file trasformato.

 Ad esempio, se il progetto di Visual Studio include un file di modello denominato **MyTemplate.tt** che contiene la direttiva seguente:

 `<#@output extension=".cs"#>`

 Visual Studio genererà un file denominato **MyTemplate.cs**

 La direttiva `output` in un modello di testo (pre-elaborato) della fase di esecuzione non è necessaria. L'applicazione otterrà la stringa generata con una chiamata a `TextTransform()`. Per altre informazioni, vedere [generazione di testo in fase di esecuzione con modelli di testo T4](../modeling/run-time-text-generation-with-t4-text-templates.md).

## <a name="using-the-output-directive"></a>Uso della direttiva output

```
<#@ output extension=".fileNameExtension" [encoding="encoding"] #>
```

 In ogni modello di testo non deve essere presente più di una direttiva `output`.

## <a name="extension-attribute"></a>attributo di estensione
 Specifica l'estensione di file del file di output di testo generato.

 Il valore predefinito è **. cs**

 Esempi: `<#@ output extension=".txt" #>`

 `<#@ output extension=".htm" #>`

 `<#@ output extension=".cs" #>`

 `<#@ output extension=".vb" #>`

 I valori accettabili: Qualsiasi estensione di file valida.

## <a name="encoding-attribute"></a>attributo di codifica
 Specifica la codifica da usare quando viene generato il file di output. Ad esempio:

 `<#@ output encoding="utf-8"#>`

 Il valore predefinito è la codifica usata dal file di modello di testo.

 Valori accettabili: `us-ascii`

 `utf-16BE`

 `utf-16`

 `utf-8`

 `utf-7`

 `utf-32`

 `0` (valore predefinito del sistema)

 In generale, è possibile usare la stringa WebName o il numero CodePage di tutte le codifiche restituite da <xref:System.Text.Encoding.GetEncodings%2A?displayProperty=fullName>.
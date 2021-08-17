---
title: Direttiva output T4
description: Si apprenderà Visual Studio modelli di testo, la direttiva di output viene usata per definire l'estensione del nome file e la codifica del file trasformato.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.technology: vs-ide-modeling
ms.workload:
- multiple
ms.openlocfilehash: b5b8bae97dbed7afbcae7611bd9787979b8ab882
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122055354"
---
# <a name="t4-output-directive"></a>Direttiva output T4

In Visual Studio di testo, la direttiva viene usata per definire l'estensione e la codifica del `output` nome file del file trasformato.

 Ad esempio, se il Visual Studio progetto include un file modello **denominato MyTemplate.tt** che contiene la direttiva seguente:

 `<#@output extension=".cs"#>`

 quindi Visual Studio genererà un file denominato **MyTemplate.cs**

 La direttiva `output` in un modello di testo (pre-elaborato) della fase di esecuzione non è necessaria. L'applicazione otterrà la stringa generata con una chiamata a `TextTransform()`. Per altre informazioni, vedere [Generazione di testo di run-time con modelli di testo T4.](../modeling/run-time-text-generation-with-t4-text-templates.md)

## <a name="using-the-output-directive"></a>Uso della direttiva output

```
<#@ output extension=".fileNameExtension" [encoding="encoding"] #>
```

 In ogni modello di testo non deve essere presente più di una direttiva `output`.

## <a name="extension-attribute"></a>attributo di estensione
 Specifica l'estensione di file del file di output di testo generato.

 Il valore predefinito è **.cs**

 Esempi: `<#@ output extension=".txt" #>`

 `<#@ output extension=".htm" #>`

 `<#@ output extension=".cs" #>`

 `<#@ output extension=".vb" #>`

 Valori accettabili: qualsiasi estensione di file valida.

## <a name="encoding-attribute"></a>attributo di codifica
 Specifica la codifica da usare quando viene generato il file di output. Esempio:

 `<#@ output encoding="utf-8"#>`

 Il valore predefinito è la codifica usata dal file di modello di testo.

 Valori accettabili: `us-ascii`

 `utf-16BE`

 `utf-16`

 `utf-8`

 `utf-7`

 `utf-32`

 `0` (Impostazione predefinita del sistema)

 In generale, è possibile usare la stringa WebName o il numero CodePage di tutte le codifiche restituite da <xref:System.Text.Encoding.GetEncodings%2A?displayProperty=fullName>.

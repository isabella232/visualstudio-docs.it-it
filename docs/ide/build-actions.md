---
title: Azioni di compilazione nei file
ms.date: 11/19/2018
ms.technology: vs-ide-compile
ms.topic: reference
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 061a3cce8d1d29b57c02de4506a809994bf12910
ms.sourcegitcommit: 59e5758036223ee866f3de5e3c0ab2b6dbae97b6
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/23/2019
ms.locfileid: "68416507"
---
# <a name="build-actions"></a>Azioni di compilazione

Tutti i file dei progetti Visual Studio includono un'azione di compilazione, che consente di controllare cosa accade ai file quando viene compilato il progetto.

> [!NOTE]
> Questo argomento si applica a Visual Studio in Windows. Per Visual Studio per Mac, vedere [Azioni di compilazione in Visual Studio per Mac](/visualstudio/mac/build-actions).

## <a name="set-a-build-action"></a>Impostare un'azione di compilazione

Per impostare l'azione di compilazione per un file, aprire le proprietà del file nella finestra **Proprietà** selezionando il file in **Esplora soluzioni** e premendo **ALT**+**INVIO**. In alternativa, fare clic con il pulsante destro del mouse sul file in **Esplora soluzioni** e scegliere **Proprietà**. Nella finestra **Proprietà** nella sezione **Avanzate** usare l'elenco a discesa accanto a **Azione compilazione** per impostare un'azione di compilazione per il file.

![Azioni di compilazione per file in Visual Studio](media/build-actions.png)

## <a name="build-action-values"></a>Valori dell'azione di compilazione

Le azioni di compilazione per i file di progetto di C# e Visual Basic includono:

* **None**: il file non fa parte della compilazione in alcun modo. Questo valore può essere usato per i file di documentazione come i file leggimi, ad esempio.
* **Compile**: il file viene passato al compilatore come file di origine.
* **Content**: un file contrassegnato come **Content** può essere recuperato come flusso chiamando <xref:System.Windows.Application.GetContentStream%2A?displayProperty=nameWithType>. Per i progetti ASP.NET, questi file vengono inclusi come parte del sito quando questo viene distribuito.
* **Embedded Resource**: il file viene passato al compilatore come una risorsa da incorporare nell'assembly. È possibile chiamare <xref:System.Reflection.Assembly.GetManifestResourceStream%2A?displayProperty=fullName> per leggere il file dall'assembly.
* **AdditionalFiles**: un file di testo non di origine che viene passato al compilatore C# o Visual Basic come input. Questa azione di compilazione viene usata principalmente per specificare input per [analizzatori](../code-quality/roslyn-analyzers-overview.md) cui viene fatto riferimento in un progetto per verificare la qualità del codice. Per altre informazioni, vedere [Use additional files](https://github.com/dotnet/roslyn/blob/master/docs/analyzers/Using%20Additional%20Files.md) (Usare file aggiuntivi).

## <a name="see-also"></a>Vedere anche

- [Opzioni del compilatore C#](/dotnet/csharp/language-reference/compiler-options/listed-alphabetically)
- [Opzioni del compilatore Visual Basic](/dotnet/visual-basic/reference/command-line-compiler/compiler-options-listed-alphabetically)
- [Azioni di compilazione (Visual Studio per Mac)](/visualstudio/mac/build-actions)
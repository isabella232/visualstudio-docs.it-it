---
title: Azioni di compilazione nei file
description: Informazioni su come tutti i file in un progetto Visual Studio hanno un'azione di compilazione e l'azione di compilazione controlla cosa accade al file quando il progetto viene compilato.
ms.custom: SEO-VS-2020
ms.date: 11/19/2018
ms.technology: vs-ide-compile
ms.topic: reference
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 9bb9678d421e9e12c3595806af1afcfe1f1fd82ad760aa3aaa3934149f59ff51
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121234057"
---
# <a name="build-actions"></a>Azioni di compilazione

Tutti i file dei progetti Visual Studio includono un'azione di compilazione, che consente di controllare cosa accade ai file quando viene compilato il progetto.

> [!NOTE]
> Questo argomento si applica a Visual Studio in Windows. Per Visual Studio per Mac, vedere [Azioni di compilazione in Visual Studio per Mac](/visualstudio/mac/build-actions).

## <a name="set-a-build-action"></a>Impostare un'azione di compilazione

Per impostare l'azione di compilazione per un file, aprire le proprietà del file nella finestra **Proprietà** selezionando il file in **Esplora soluzioni** e premendo **ALT**+**INVIO**. In alternativa, fare clic con il pulsante destro del mouse sul file in **Esplora soluzioni** e scegliere **Proprietà**. Nella finestra **Proprietà** nella sezione **Avanzate** usare l'elenco a discesa accanto a **Azione compilazione** per impostare un'azione di compilazione per il file.

![Azioni di compilazione per file in Visual Studio](media/build-actions.png)

## <a name="build-action-values"></a>Valori dell'azione di compilazione

Alcune delle azioni di compilazione più comuni per i file di progetto di C# e Visual Basic includono:

|Azione di compilazione | Tipi di progetto | Descrizione |
|-|-|
| **AdditionalFiles** | C#, Visual Basic | Un file di testo non di origine che viene passato al compilatore C# o Visual Basic come input. Questa azione di compilazione viene usata principalmente per specificare input per [analizzatori](../code-quality/roslyn-analyzers-overview.md) cui viene fatto riferimento in un progetto per verificare la qualità del codice. Per altre informazioni, vedere [Use additional files](https://github.com/dotnet/roslyn/blob/master/docs/analyzers/Using%20Additional%20Files.md) (Usare file aggiuntivi).|
| **ApplicationDefinition** | WPF | File che definisce l'applicazione. Quando si crea un progetto per la prima volta, si tratta del file *App.xaml*. |
| **CodeAnalysisDictionary** | .NET | Dizionario di parole personalizzato, usato dall'analisi codice per il controllo ortografico. Vedere [Procedura: Personalizzare il Code Analysis personalizzato](../code-quality/how-to-customize-the-code-analysis-dictionary.md)|
| **Compilazione** | any | Il file viene passato al compilatore come file di origine.|
| **Contenuto** | .NET | Un file contrassegnato come **Content** può essere recuperato come flusso chiamando <xref:System.Windows.Application.GetContentStream%2A?displayProperty=nameWithType>. Per i progetti ASP.NET, questi file vengono inclusi come parte del sito quando questo viene distribuito.|
| **DesignData** | WPF | Usato per i file ViewModel XAML, per consentire la visualizzazione dei controlli utente in fase di progettazione, con tipi fittizi e dati di esempio. |
| **DesignDataWithDesignTimeCreateable** | WPF | Come **DesignData**, ma con tipi effettivi.  |
| **Embedded Resource** | .NET | Il file viene passato al compilatore come una risorsa da incorporare nell'assembly. È possibile chiamare <xref:System.Reflection.Assembly.GetManifestResourceStream%2A?displayProperty=fullName> per leggere il file dall'assembly.|
| **EntityDeploy** | .NET | Per Entity Framework (EF) file con estensione EDMX che specificano la distribuzione di artefatti EF. |
| **Fakes** | .NET | Usato per il framework di test di Microsoft Fakes. Vedere [Isolare codice sottoposto a test con Microsoft Fakes](../test/isolating-code-under-test-with-microsoft-fakes.md) |
| **Nessuno** | any | Il file non fa parte della compilazione in alcun modo. Questo valore può essere usato per i file di documentazione come i file leggimi, ad esempio.|
| **Page** | WPF | Compilare un file XAML in un file binario con estensione baml per un caricamento più rapido in fase di esecuzione. |
| **Risorsa** | WPF | Specifica di incorporare il file in un file di risorse del manifesto dell'assembly con estensione *.g.resources*. |
| **Shadow** | .NET | Usato per un file con estensione accessor contenente un elenco di nomi file di assembly compilati, uno per riga. Per ogni assembly nell'elenco, generare classi pubbliche con i nomi `ClassName_Accessor` che sono esattamente come gli originali, ma con metodi pubblici anziché metodi privati. Usato per il testing unità. |
| **Schermata iniziale** | WPF | Specifica un file di immagine da visualizzare in fase di esecuzione all'avvio dell'app. |
| **XamlAppDef** | Windows Workflow Foundation | Indica alla compilazione di compilare un file XAML del flusso di lavoro in un assembly con un flusso di lavoro incorporato. |

> [!NOTE]
> È possibile definire azioni di compilazione aggiuntive per tipi di progetto specifici, pertanto l'elenco di azioni di compilazione dipende dal tipo di progetto e potrebbero venire visualizzati valori che non sono presenti in questo elenco.

## <a name="see-also"></a>Vedi anche

- [Opzioni del compilatore C#](/dotnet/csharp/language-reference/compiler-options/listed-alphabetically)
- [Opzioni del compilatore Visual Basic](/dotnet/visual-basic/reference/command-line-compiler/compiler-options-listed-alphabetically)
- [Azioni di compilazione (Visual Studio per Mac)](/visualstudio/mac/build-actions)

---
title: Implementazione della colorazione della sintassi | Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- syntax coloring, implementing
- editors [Visual Studio SDK], colorizing text
- text, colorizing in editors
ms.assetid: 96e762ca-efd0-41e7-8958-fda4897c8c7a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bb3f26f59d7cbc994da1d2537e0ab352ce12205e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "85905201"
---
# <a name="implementing-syntax-coloring"></a>Implementazione della colorazione della sintassi
Quando il servizio di linguaggio fornisce la colorazione della sintassi, il parser converte una riga di testo in una matrice di elementi colorabili e restituisce i tipi di token corrispondenti a tali elementi colorabili. Il parser deve restituire i tipi di token che appartengono a un elenco di elementi colorabili. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Visualizza ogni elemento colorabile nella finestra del codice in base agli attributi assegnati dall'oggetto Colorer al tipo di token appropriato.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] non specifica un'interfaccia del parser e l'implementazione del parser è completa. Viene tuttavia fornita un'implementazione del parser predefinita nel progetto di pacchetto del linguaggio di Visual Studio. Per il codice gestito, il Framework di pacchetto gestito (MPF) fornisce il supporto completo per la colorazione del testo.

 I servizi di linguaggio legacy sono implementati come parte di un pacchetto VSPackage, ma il modo più recente per implementare le funzionalità del servizio di linguaggio consiste nell'usare le estensioni MEF. Per ulteriori informazioni sul nuovo modo per implementare la colorazione della sintassi, vedere [procedura dettagliata: evidenziazione del testo](../../extensibility/walkthrough-highlighting-text.md).

> [!NOTE]
> Si consiglia di iniziare a usare la nuova API editor appena possibile. Ciò consente di migliorare le prestazioni del servizio di linguaggio e di sfruttare i vantaggi delle nuove funzionalità dell'editor.

## <a name="steps-followed-by-an-editor-to-colorize-text"></a>Passaggi seguiti da un editor per colorare il testo

1. L'editor ottiene il colorante chiamando il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A> metodo sull' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> oggetto.

2. L'editor chiama il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.GetStateMaintenanceFlag%2A> metodo per determinare se il coloratore necessita dello stato di ogni riga da mantenere all'esterno del coloratore.

3. Se il coloratore richiede che lo stato venga mantenuto all'esterno del coloratore, l'editor chiama il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.GetStartState%2A> metodo per ottenere lo stato della prima riga.

4. Per ogni riga nel buffer, l'editor chiama il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> metodo, che esegue i passaggi seguenti:

    1. La riga di testo viene passata a uno scanner per convertire il testo in token. Ogni token specifica il testo del token e il tipo di token.

    2. Il tipo di token viene convertito in un indice in un elenco di elementi colorabili.

    3. Le informazioni sul token vengono usate per compilare una matrice in modo che ogni elemento della matrice corrisponda a un carattere nella riga. I valori archiviati nella matrice sono gli indici nell'elenco elementi colorabili.

    4. Lo stato alla fine della riga viene restituito per ogni riga.

5. Se il coloratore richiede che lo stato sia mantenuto, l'editor memorizza nella cache lo stato della riga.

6. L'editor esegue il rendering della riga di testo utilizzando le informazioni restituite dal <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> metodo. La procedura da adottare è la seguente:

    1. Per ogni carattere nella riga, ottenere l'indice dell'elemento colorabile.

    2. Se si usano gli elementi colorabili predefiniti, accedere all'elenco di elementi colorabili dell'editor.

    3. In caso contrario, chiamare il metodo del servizio <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A> di linguaggio per ottenere un elemento colorabile.

    4. Usare le informazioni nell'elemento colorabile per eseguire il rendering del testo nella visualizzazione.

## <a name="managed-package-framework-colorizer"></a>Color Framework del pacchetto gestito
 Il Framework di pacchetto gestito (MPF) fornisce tutte le classi necessarie per implementare un colorante. La classe del servizio di linguaggio deve ereditare la <xref:Microsoft.VisualStudio.Package.LanguageService> classe e implementare i metodi richiesti. È necessario fornire uno scanner e un parser implementando l' <xref:Microsoft.VisualStudio.Package.IScanner> interfaccia e restituire un'istanza di tale interfaccia dal <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> Metodo (uno dei metodi che devono essere implementati nella <xref:Microsoft.VisualStudio.Package.LanguageService> classe). Per ulteriori informazioni, vedere [colorazione della sintassi in un servizio di linguaggio legacy](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md).

## <a name="see-also"></a>Vedere anche
- [Procedura: Usare gli elementi colorabili incorporati](../../extensibility/internals/how-to-use-built-in-colorable-items.md)
- [Elementi colorabili personalizzati](../../extensibility/internals/custom-colorable-items.md)
- [Sviluppo di un servizio di linguaggio legacy](../../extensibility/internals/developing-a-legacy-language-service.md)
- [Colorazione della sintassi in un servizio di linguaggio legacy](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)

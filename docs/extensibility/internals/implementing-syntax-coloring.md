---
title: Implementazione della colorazione della sintassi | Microsoft Docs
description: Informazioni su come implementare la colorazione della Visual Studio usando le funzionalità del servizio di linguaggio del framework del pacchetto gestito (MPF).
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- syntax coloring, implementing
- editors [Visual Studio SDK], colorizing text
- text, colorizing in editors
ms.assetid: 96e762ca-efd0-41e7-8958-fda4897c8c7a
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: fd8686ddae6654ab4ff1411c21b342b77ba4ba65
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122049987"
---
# <a name="implementing-syntax-coloring"></a>Implementazione della colorazione della sintassi
Quando il servizio di linguaggio fornisce la colorazione della sintassi, il parser converte una riga di testo in una matrice di elementi colorabili e restituisce i tipi di token corrispondenti a questi elementi colorabili. Il parser deve restituire i tipi di token che appartengono a un elenco di elementi colorabili. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] visualizza ogni elemento colorabile nella finestra del codice in base agli attributi assegnati dall'oggetto colorizer al tipo di token appropriato.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] non specifica un'interfaccia del parser e l'implementazione del parser è completamente a parte l'utente. Tuttavia, un'implementazione del parser predefinita viene fornita nel progetto Visual Studio Language Package. Per il codice gestito, il framework del pacchetto gestito (MPF) fornisce il supporto completo per la colorazione del testo.

 I servizi di linguaggio legacy vengono implementati come parte di un PACCHETTO VSPackage, ma il modo più recente per implementare le funzionalità del servizio di linguaggio è usare le estensioni MEF. Per altre informazioni sul nuovo modo di implementare la colorazione della sintassi, vedere [Procedura dettagliata: Evidenziazione del testo.](../../extensibility/walkthrough-highlighting-text.md)

> [!NOTE]
> È consigliabile iniziare a usare la nuova API dell'editor appena possibile. Ciò consente di migliorare le prestazioni del servizio di linguaggio e di sfruttare le nuove funzionalità dell'editor.

## <a name="steps-followed-by-an-editor-to-colorize-text"></a>Passaggi seguiti da un editor per colorare il testo

1. L'editor ottiene il colorizer chiamando <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A> il metodo <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> sull'oggetto .

2. L'editor chiama il metodo per determinare se il colorista deve mantenere lo stato di ogni <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.GetStateMaintenanceFlag%2A> riga all'esterno del colorizer.

3. Se il colorista richiede che lo stato sia mantenuto all'esterno del colorizer, l'editor chiama il metodo per ottenere <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.GetStartState%2A> lo stato della prima riga.

4. Per ogni riga nel buffer, l'editor chiama il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> metodo , che esegue i passaggi seguenti:

    1. La riga di testo viene passata a uno scanner per convertire il testo in token. Ogni token specifica il testo del token e il tipo di token.

    2. Il tipo di token viene convertito in un indice in un elenco di elementi colorabili.

    3. Le informazioni sul token vengono usate per compilare una matrice in modo che ogni elemento della matrice corrisponda a un carattere nella riga. I valori archiviati nella matrice sono gli indici nell'elenco di elementi colorabili.

    4. Lo stato alla fine della riga viene restituito per ogni riga.

5. Se il colorista richiede che lo stato sia mantenuto, l'editor memorizza nella cache lo stato per tale riga.

6. L'editor esegue il rendering della riga di testo usando le informazioni restituite dal <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> metodo . La procedura da adottare è la seguente:

    1. Per ogni carattere nella riga, ottenere l'indice dell'elemento colorabile.

    2. Se si usano gli elementi colorabili predefiniti, accedere all'elenco di elementi colorabili dell'editor.

    3. In caso contrario, chiamare il metodo del servizio <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A> di linguaggio per ottenere un elemento colorabile.

    4. Usare le informazioni nell'elemento colorabile per eseguire il rendering del testo nella visualizzazione.

## <a name="managed-package-framework-colorizer"></a>Colorizer del framework di pacchetti gestiti
 Il framework del pacchetto gestito (MPF) fornisce tutte le classi necessarie per implementare un colorizer. La classe del servizio di linguaggio deve <xref:Microsoft.VisualStudio.Package.LanguageService> ereditare la classe e implementare i metodi necessari. È necessario fornire uno scanner e un parser implementando l'interfaccia e restituire un'istanza di tale interfaccia dal metodo (uno dei metodi che devono <xref:Microsoft.VisualStudio.Package.IScanner> <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> essere implementati nella classe <xref:Microsoft.VisualStudio.Package.LanguageService> ). Per altre informazioni, vedere [Colorazione della sintassi in un servizio di linguaggio legacy.](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)

## <a name="see-also"></a>Vedi anche
- [Procedura: Usare gli elementi colorabili incorporati](../../extensibility/internals/how-to-use-built-in-colorable-items.md)
- [Elementi colorabili personalizzati](../../extensibility/internals/custom-colorable-items.md)
- [Sviluppo di un servizio di linguaggio legacy](../../extensibility/internals/developing-a-legacy-language-service.md)
- [Colorazione della sintassi in un servizio di linguaggio legacy](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)

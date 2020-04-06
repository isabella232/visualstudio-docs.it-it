---
title: Implementazione della colorazione della sintassi Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
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
ms.openlocfilehash: 83ce66dd6a31e3ef852feb91e2ba304e6688a723
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707638"
---
# <a name="implementing-syntax-coloring"></a>Implementazione della colorazione della sintassi
Quando il servizio di linguaggio fornisce la colorazione della sintassi, il parser converte una riga di testo in una matrice di elementi colorabili e restituisce i tipi di token corrispondenti a questi elementi colorabili. Il parser deve restituire i tipi di token che appartengono a un elenco di elementi colorabili. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]visualizza ogni elemento colorabile nella finestra del codice in base agli attributi assegnati dall'oggetto colorizer al tipo di token appropriato.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]non specifica un'interfaccia del parser e l'implementazione del parser è completamente all'utente. Tuttavia, un'implementazione del parser predefinito viene fornita nel progetto di Visual Studio Language Package.However, a default parser implementation is provided in the Visual Studio Language Package project. Per il codice gestito, il framework del pacchetto gestito (MPF) fornisce il supporto completo per la colorazione del testo.

 Servizi di linguaggio legacy vengono implementati come parte di un VSPackage, ma il modo più recente per implementare le funzionalità del servizio di linguaggio consiste nell'utilizzare le estensioni MEF. Per ulteriori informazioni sul nuovo modo di implementare la colorazione della sintassi, vedere [Procedura dettagliata: evidenziazione del testo](../../extensibility/walkthrough-highlighting-text.md).

> [!NOTE]
> Si consiglia di iniziare a utilizzare la nuova API dell'editor il prima possibile. Ciò migliorerà le prestazioni del servizio di linguaggio e consentirà di sfruttare le nuove funzionalità dell'editor.

## <a name="steps-followed-by-an-editor-to-colorize-text"></a>Passaggi seguiti da un editor per colorare il testo

1. L'editor ottiene il colorizer chiamando il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A> metodo sull'oggetto. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo>

2. L'editor <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.GetStateMaintenanceFlag%2A> chiama il metodo per determinare se il colorizer necessita dello stato di ogni riga da mantenere al di fuori del colorizer.

3. Se il colorizer richiede che lo stato venga mantenuto <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.GetStartState%2A> all'esterno del colorizer, l'editor chiama il metodo per ottenere lo stato della prima riga.

4. Per ogni riga nel buffer, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> l'editor chiama il metodo , che esegue i passaggi seguenti:

    1. La riga di testo viene passata a uno scanner per convertire il testo in token. Ogni token specifica il testo del token e il tipo di token.

    2. Il tipo di token viene convertito in un indice in un elenco di elementi colorabili.

    3. Le informazioni sul token vengono utilizzate per compilare una matrice in modo che ogni elemento della matrice corrisponda a un carattere nella riga. I valori memorizzati nella matrice sono gli indici nell'elenco di elementi colorabili.

    4. Lo stato alla fine della riga viene restituito per ogni riga.

5. Se il colorizer richiede che lo stato venga mantenuto, l'editor memorizza nella cache lo stato per tale riga.

6. L'editor esegue il rendering della riga <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> di testo utilizzando le informazioni restituite dal metodo. La procedura da adottare è la seguente:

    1. Per ogni carattere nella riga, ottenere l'indice dell'elemento colorabile.

    2. Se si utilizzano gli elementi colorabili predefiniti, accedere all'elenco degli elementi colorabili dell'editor.

    3. In caso contrario, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A> chiamare il metodo del servizio di linguaggio per ottenere un elemento colorabile.

    4. Utilizzate le informazioni nell'elemento colorabile per eseguire il rendering del testo nella visualizzazione.

## <a name="managed-package-framework-colorizer"></a>Colorizer framework di pacchetto gestitoManaged Package Framework Colorizer
 Il framework del pacchetto gestito (MPF) fornisce tutte le classi necessarie per implementare un colorizzatore. La classe del servizio <xref:Microsoft.VisualStudio.Package.LanguageService> di linguaggio deve ereditare la classe e implementare i metodi necessari. È necessario fornire uno scanner <xref:Microsoft.VisualStudio.Package.IScanner> e un parser implementando l'interfaccia e restituire un'istanza di tale interfaccia dal <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> metodo (uno dei metodi che devono essere implementati nella <xref:Microsoft.VisualStudio.Package.LanguageService> classe). Per ulteriori informazioni, vedere [Colorazione della sintassi in un servizio](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)di linguaggio Legacy .

## <a name="see-also"></a>Vedere anche
- [Procedura: Usare gli elementi colorabili incorporati](../../extensibility/internals/how-to-use-built-in-colorable-items.md)
- [Elementi colorabili personalizzati](../../extensibility/internals/custom-colorable-items.md)
- [Sviluppo di un servizio di linguaggio legacy](../../extensibility/internals/developing-a-legacy-language-service.md)
- [Colorazione della sintassi in un servizio di linguaggio legacy](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)

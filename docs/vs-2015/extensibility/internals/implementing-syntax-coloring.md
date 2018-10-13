---
title: Implementazione della colorazione della sintassi | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- syntax coloring, implementing
- editors [Visual Studio SDK], colorizing text
- text, colorizing in editors
ms.assetid: 96e762ca-efd0-41e7-8958-fda4897c8c7a
caps.latest.revision: 21
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: a4315b9e6b6fdb12a0fcb3e97f6b208d6b84acd9
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49259254"
---
# <a name="implementing-syntax-coloring"></a>Implementazione della colorazione della sintassi
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Quando il servizio di linguaggio fornisce la colorazione della sintassi, il parser converte una riga di testo in una matrice di elementi colorabili e restituisce i tipi di token corrispondenti a questi elementi colorabili. Il parser deve restituire tipi di token che appartengono a un elenco di elementi colorabili. [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Consente di visualizzare ogni elemento colorabile nella finestra del codice in base agli attributi assegnati dall'oggetto colorizzatore per il tipo di token appropriato.  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] non specifica un'interfaccia, parser e implementazione di parser è responsabilità dell'utente. Tuttavia, un'implementazione di parser predefinita viene fornita nel progetto di Visual Studio Language Pack. Per codice gestito, il framework di pacchetto gestito (MPF) fornisce supporto completo per la colorazione del testo.  
  
 Servizi di linguaggio legacy vengono implementati come parte di un pacchetto VSPackage, ma il modo più recente per implementare le funzionalità del servizio di linguaggio consiste nell'usare le estensioni MEF. Per altre informazioni sul nuovo modo per implementare la colorazione della sintassi, vedere [procedura dettagliata: evidenziazione testo](../../extensibility/walkthrough-highlighting-text.md).  
  
> [!NOTE]
>  È consigliabile che si inizia a usare il nuovo editor delle API appena possibile. Verrà migliorare le prestazioni del servizio di linguaggio e consentono di sfruttare nuove funzionalità dell'editor.  
  
## <a name="steps-followed-by-an-editor-to-colorize-text"></a>Passaggi seguiti da un Editor per colorare il testo  
  
1.  L'editor Ottiene il colorizzatore chiamando il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A> metodo su di <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> oggetto.  
  
2.  Le chiamate di editor la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.GetStateMaintenanceFlag%2A> metodo per determinare se il colorizzatore richiede lo stato di ogni riga venga mantenuto di fuori il colorizzatore.  
  
3.  Se il colorizzatore richiede lo stato venga mantenuto di fuori il colorizzatore, l'editor chiama il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.GetStartState%2A> metodo per ottenere lo stato della prima riga.  
  
4.  Per ogni riga nel buffer, chiama l'editor di <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> metodo, che esegue i passaggi seguenti:  
  
    1.  La riga di testo viene passata a uno scanner per convertire il testo in token. Ogni token specifica il testo del token e il tipo di token.  
  
    2.  Il tipo di token viene convertito in un indice in un elenco di elementi colorabili.  
  
    3.  Le informazioni del token viene utilizzate per compilare una matrice in modo che ogni elemento della matrice corrisponde a un carattere nella riga. I valori archiviati nella matrice sono gli indici nell'elenco di elementi colorabili.  
  
    4.  Viene restituito lo stato alla fine della riga per ogni riga.  
  
5.  Se il colorizzatore richiede lo stato venga mantenuto, l'editor memorizza nella cache lo stato per tale riga.  
  
6.  L'editor esegue il rendering della riga di testo utilizzando le informazioni restituite dal <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> (metodo). La procedura da adottare è la seguente:  
  
    1.  Per ogni carattere nella riga, ottenere l'indice dell'elemento colorabile.  
  
    2.  Se si usa gli elementi colorabili predefiniti, accedere a elenco di elementi colorabili dell'editor.  
  
    3.  In caso contrario, chiamare il servizio di linguaggio <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A> metodo per ottenere un elemento colorabile.  
  
    4.  Usare le informazioni dell'elemento colorabile per il rendering del testo nella visualizzazione.  
  
## <a name="managed-package-framework-colorizer"></a>Colorizzatore Framework di pacchetto gestito  
 Il framework di pacchetto gestito (MPF) fornisce tutte le classi necessarie per implementare un colorizzatore. Classe del servizio di linguaggio deve ereditare il <xref:Microsoft.VisualStudio.Package.LanguageService> classe e implementare i metodi richiesti. È necessario fornire un scanner e parser implementando la <xref:Microsoft.VisualStudio.Package.IScanner> interfaccia e restituire un'istanza di tale interfaccia dal <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> metodo (uno dei metodi che devono essere implementati nel <xref:Microsoft.VisualStudio.Package.LanguageService> classe). Per altre informazioni, vedere [colorazione della sintassi in un servizio di linguaggio Legacy](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura: usare elementi colorabili incorporati](../../extensibility/internals/how-to-use-built-in-colorable-items.md)   
 [Elementi colorabili personalizzati](../../extensibility/internals/custom-colorable-items.md)   
 [Sviluppo di un servizio di linguaggio Legacy](../../extensibility/internals/developing-a-legacy-language-service.md)   
 [Colorazione della sintassi in un servizio di linguaggio legacy](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)


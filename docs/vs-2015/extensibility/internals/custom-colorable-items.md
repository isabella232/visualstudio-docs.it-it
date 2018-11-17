---
title: Elementi colorabili personalizzati | Microsoft Docs
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
- colorable items
- language services, custom colorable items
ms.assetid: b4d0ddee-c04b-48dc-ba82-f6068570cef0
caps.latest.revision: 25
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 272d16b9f5f8fb33b68c911c5e7bd27923f4c2db
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/16/2018
ms.locfileid: "51796948"
---
# <a name="custom-colorable-items"></a>Elementi colorabili personalizzati
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

È possibile sostituire l'elenco dei tipi per colorare, quali parole chiave e i commenti, mediante l'implementazione di elementi colorabili personalizzati come parte del servizio di linguaggio.  
  
## <a name="user-settings-of-colorable-items"></a>Impostazioni utente di elementi colorabili  
 È possibile visualizzare il **tipi di carattere e colori** finestra di dialogo selezionando **opzioni** sul **strumenti** menu e selezionando **Fonts and Colors** sotto **ambiente**. Quando si seleziona una visualizzazione, ad esempio **Editor di testo** oppure **finestra di comando**, il **elementi visualizzati** casella di riepilogo Mostra tutti gli elementi colorabili per tale visualizzazione. È possibile visualizzare e modificare il tipo di carattere, dimensioni, colore di primo piano e colore di sfondo per ogni elemento colorabile. Le scelte sono archiviate in una cache nel Registro di sistema e a cui accede il nome dell'elemento colorabile.  
  
## <a name="presentation-of-colorable-items"></a>Presentazione di elementi colorabili  
 Poiché l'IDE gestisce l'override dell'utente di elementi colorabili nella **Fonts and Colors** finestra di dialogo, è necessario fornire solo ogni elemento colorabile personalizzato con un nome. Questo nome viene visualizzato un messaggio nel **elementi visualizzati** elenco. Gli elementi colorabili vengono visualizzati in ordine alfabetico. Per raggruppare elementi colorabili personalizzati del servizio di linguaggio, è possibile iniziare ogni nome con il nome del linguaggio, ad esempio **NewLanguage - commento** e **NewLanguage - parola chiave**.  
  
> [!CAUTION]
>  È necessario includere il nome della lingua nel nome dell'elemento colorabile per evitare conflitti con nomi di elemento colorabile esistenti. Se si modifica il nome di uno degli elementi colorabili durante lo sviluppo, è necessario reimpostare la cache che è stata creata la prima volta che gli elementi colorabili erano accessibili. È possibile reimpostare la cache sperimentale con lo strumento CreateExpInstance con cui viene installato con Visual Studio SDK, in genere nella directory  
>   
>  **C:\Programmi\Microsoft file (x86) \Microsoft Visual Studio 14.0\VSSDK\VisualStudioIntegration\Tools\Bin**  
>   
>  Per reimpostare la cache, chiamare `CreateExpInstance /Reset`. Per altre informazioni sulle CreateExpInstance, vedere [CreateExpInstance Utility](../../extensibility/internals/createexpinstance-utility.md).  
  
 Il primo elemento nell'elenco di elementi colorabili non viene mai fatto riferimento. Il primo elemento corrisponde a un indice colorabile dell'elemento pari a 0, e [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] sempre fornisce i colori del testo predefinito e attributi per quell'elemento. Il modo più semplice di gestione di questo elemento privo di riferimento è di fornire un elemento colorabile segnaposto nell'elenco come primo elemento.  
  
## <a name="implementing-custom-colorable-items"></a>Implementazione di elementi colorabili personalizzati  
  
1. Definire cosa deve essere colorata nel linguaggio, ad esempio parole chiave, operatore e identificatore.  
  
2. Creare un'enumerazione di questi elementi colorabili.  
  
3. Associare i tipi di token restituiti da un parser o dello scanner con i valori enumerati.  
  
    I valori che rappresentano i tipi di token, ad esempio, potrebbero essere gli stessi valori dell'enumerazione di elementi colorabili personalizzati.  
  
4. Nell'implementazione del <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> metodo nella <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> oggetto, compilare l'elenco di attributi con i valori dell'enumerazione di elementi colorabili personalizzati corrispondente per i tipi di token restituiti dal parser o dello scanner.  
  
5. Nella stessa classe che implementa il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> l'interfaccia, implementare il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems> interfaccia e i relativi due metodi <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetItemCount%2A> e <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A>.  
  
6. Implementare l'interfaccia <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem>.  
  
7. Se si desidera supportare valori di colore a 24 bit o ad alta, implementare anche il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> interfaccia.  
  
8. Nell'oggetto servizio di linguaggio, creare un elenco che contiene il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem> oggetti, uno per ogni elemento colorabile possibile identificare il parser o lo scanner.  
  
    È possibile accedere a ogni elemento nell'elenco usando il valore corrispondente dall'enumerazione di elementi colorabili personalizzati. Usare i valori di enumerazione come indice nell'elenco. Il primo elemento nell'elenco non viene mai eseguito l'accesso, poiché per il testo predefinito corrisponde allo stile [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] sempre gestisce se stesso. Possibile rimediare a questo mediante l'inserimento di un elemento colorabile segnaposto all'inizio dell'elenco.  
  
9. Nell'implementazione del metodo di <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetItemCount%2A> (metodo), restituiscono il numero di elementi nell'elenco di elementi colorabili personalizzati.  
  
10. Nell'implementazione del <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A> (metodo), restituiscono l'elemento colorabile richiesto dall'elenco.  
  
    Per un esempio di come implementare il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem> e <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> interfacce, vedere <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem>.  
  
## <a name="see-also"></a>Vedere anche  
 [Modello di un servizio di linguaggio Legacy](../../extensibility/internals/model-of-a-legacy-language-service.md)   
 [Colorazione della sintassi negli editor personalizzati](../../extensibility/syntax-coloring-in-custom-editors.md)   
 [Colorazione della sintassi in un servizio di linguaggio Legacy](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)   
 [Implementazione della colorazione della sintassi](../../extensibility/internals/implementing-syntax-coloring.md)   
 [Procedura: Usare gli elementi colorabili incorporati](../../extensibility/internals/how-to-use-built-in-colorable-items.md)


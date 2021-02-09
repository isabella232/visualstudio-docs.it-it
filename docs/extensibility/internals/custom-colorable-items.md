---
title: Elementi colorabili personalizzati | Microsoft Docs
description: Informazioni su come creare elementi colorabili personalizzati come parte di un servizio di linguaggio eseguendo l'override degli elementi nella finestra di dialogo tipi di carattere e colori, ad esempio parole chiave e commenti.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- colorable items
- language services, custom colorable items
ms.assetid: b4d0ddee-c04b-48dc-ba82-f6068570cef0
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 7df029be478fef3cf1e9b6138456986016465d5d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99903009"
---
# <a name="custom-colorable-items"></a>Elementi colorabili personalizzati
È possibile eseguire l'override dell'elenco di tipi per la colorazione, ad esempio parole chiave e commenti, implementando elementi colorabili personalizzati come parte del servizio di linguaggio.

## <a name="user-settings-of-colorable-items"></a>Impostazioni utente degli elementi colorabili
 Per visualizzare la finestra di dialogo **tipi di carattere e colori** , scegliere **Opzioni** dal menu **strumenti** e quindi selezionare **tipi di carattere e colori** in **ambiente**. Quando si seleziona una visualizzazione, ad esempio **editor di testo** o **finestra di comando**, nella casella di riepilogo **elementi visualizzati** vengono visualizzati tutti gli elementi colorabili per tale visualizzazione. È possibile visualizzare e modificare il tipo di carattere, le dimensioni, il colore di primo piano e il colore di sfondo per ogni elemento colorabile. Le scelte vengono archiviate in una cache nel registro di sistema e accessibili dal nome dell'elemento colorabile.

## <a name="presentation-of-colorable-items"></a>Presentazione di elementi colorabili
 Poiché l'IDE gestisce le sostituzioni utente degli elementi colorabili nella finestra di dialogo **tipi di carattere e colori** , è necessario fornire solo ogni elemento colorabile personalizzato con un nome. Questo nome viene visualizzato nell'elenco **elementi visualizzati** . Gli elementi colorabili sono visualizzati in ordine alfabetico. Per raggruppare gli elementi colorabili personalizzati del servizio di linguaggio, è possibile iniziare ogni nome con il nome della lingua, ad esempio **NewLanguage-comment** e **NewLanguage-keyword**.

> [!CAUTION]
> Per evitare conflitti con i nomi degli elementi colorabili esistenti, è necessario includere il nome della lingua nel nome dell'elemento colorabile. Se si modifica il nome di uno degli elementi colorabili durante lo sviluppo, è necessario reimpostare la cache che è stata creata la prima volta che è stato eseguito l'accesso agli elementi colorabili. È possibile reimpostare la cache sperimentale con lo strumento **CreateExpInstance** , installato con Visual Studio SDK, che in genere si trova nella directory:
>
> *C:\Programmi (x86) \Microsoft Visual Studio 14.0 \ VSSDK\VisualStudioIntegration\Tools\Bin*
>
> Per reimpostare la cache, immettere **CreateExpInstance/Reset**. Per ulteriori informazioni su **CreateExpInstance**, vedere [utilità CreateExpInstance](../../extensibility/internals/createexpinstance-utility.md).

 Non viene mai fatto riferimento al primo elemento dell'elenco di elementi colorabili. Il primo elemento corrisponde a un indice di elemento colorabile di 0 e [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] fornisce sempre gli attributi e i colori del testo predefiniti per tale elemento. Il modo più semplice per gestire questo elemento senza riferimenti consiste nel fornire un elemento colorabile del segnaposto nell'elenco come primo elemento.

## <a name="implement-custom-colorable-items"></a>Implementare elementi colorabili personalizzati

1. Definire gli elementi che devono essere colorati nel linguaggio, ad esempio parola chiave, operatore e identificatore.

2. Creare un'enumerazione di questi elementi colorabili.

3. Associare i tipi di token restituiti da un parser o da uno scanner con i valori enumerati.

    Ad esempio, i valori che rappresentano i tipi di token possono essere gli stessi nell'enumerazione degli elementi colorabili personalizzati.

4. Nell'implementazione del <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> metodo nell' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> oggetto, compilare l'elenco degli attributi con i valori dell'enumerazione degli elementi colorabili personalizzati corrispondente ai tipi di token restituiti dal parser o dallo scanner.

5. Nella stessa classe che implementa l' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> interfaccia, implementare l' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems> interfaccia e i relativi due metodi, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetItemCount%2A> e <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A> .

6. Implementare l'interfaccia <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem>.

7. Se si desidera supportare i valori di colore a 24 bit o alto, implementare anche l' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> interfaccia.

8. Nell'oggetto servizio di linguaggio creare un elenco contenente <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem> gli oggetti, uno per ogni elemento colorabile che il parser o lo scanner è in grado di identificare.

    È possibile accedere a ogni elemento dell'elenco usando il valore corrispondente dell'enumerazione di elementi colorabili personalizzati. Utilizzare i valori di enumerazione come indice nell'elenco. Il primo elemento dell'elenco non è mai accessibile, perché corrisponde allo stile di testo predefinito che [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] gestisce sempre se stesso. È possibile compensare questa operazione inserendo un elemento colorabile segnaposto all'inizio dell'elenco.

9. Nell'implementazione del <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetItemCount%2A> metodo, restituire il numero di elementi nell'elenco elementi colorabili personalizzati.

10. Nell'implementazione del <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A> metodo, restituire l'elemento colorabile richiesto dall'elenco.

    Per un esempio di come implementare le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem> interfacce e <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> , vedere <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> .

## <a name="see-also"></a>Vedi anche
- [Modello di un servizio di linguaggio legacy](../../extensibility/internals/model-of-a-legacy-language-service.md)
- [Colorazione della sintassi negli editor personalizzati](../../extensibility/syntax-coloring-in-custom-editors.md)
- [Colorazione della sintassi in un servizio di linguaggio legacy](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)
- [Implementare la colorazione della sintassi](../../extensibility/internals/implementing-syntax-coloring.md)
- [Procedura: utilizzare elementi colorabili incorporati](../../extensibility/internals/how-to-use-built-in-colorable-items.md)

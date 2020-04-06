---
title: Elementi colorabili personalizzati Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- colorable items
- language services, custom colorable items
ms.assetid: b4d0ddee-c04b-48dc-ba82-f6068570cef0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: feecd9e8f8178045f66999b775e2d0792f50b288
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708989"
---
# <a name="custom-colorable-items"></a>Elementi colorabili personalizzati
È possibile eseguire l'override dell'elenco di tipi per la colorazione, ad esempio parole chiave e commenti, implementando elementi colorabili personalizzati come parte del servizio di linguaggio.

## <a name="user-settings-of-colorable-items"></a>Impostazioni utente degli elementi colorabili
 È possibile visualizzare la finestra di dialogo Tipi di carattere **e colori** scegliendo **Opzioni** dal menu **Strumenti,** quindi **Tipi di carattere e colori** in **Ambiente**. Quando si seleziona una visualizzazione, ad esempio **Editor** di testo o **Finestra di comando**, nella casella di riepilogo Elementi **visualizzati** vengono visualizzati tutti gli elementi colorabili per tale visualizzazione. È possibile visualizzare e modificare il tipo di carattere, le dimensioni, il colore di primo piano e il colore di sfondo per ogni elemento colorabile. Le scelte vengono memorizzate in una cache nel Registro di sistema e vi si accede tramite il nome dell'elemento colorabile.

## <a name="presentation-of-colorable-items"></a>Presentazione di elementi colorabili
 Poiché l'IDE gestisce le sostituzioni utente di elementi colorabili nel tipi di **carattere e colori** finestra di dialogo, è necessario fornire solo ogni elemento colorabile personalizzato con un nome. Questo nome viene visualizzato nell'elenco **Elementi visualizzati.** Gli elementi colorabili vengono visualizzati in ordine alfabetico. Per raggruppare gli elementi colorabili personalizzati del servizio di linguaggio, è possibile iniziare ogni nome con il nome della lingua, ad esempio **NewLanguage - Comment** e **NewLanguage - Keyword**.

> [!CAUTION]
> È necessario includere il nome della lingua nel nome dell'elemento colorabile per evitare conflitti con i nomi degli elementi colorabili esistenti. Se si modifica il nome di uno degli elementi colorabili durante lo sviluppo, è necessario reimpostare la cache creata al primo accesso agli elementi colorabili. È possibile reimpostare la cache sperimentale con lo strumento **CreateExpInstance,** installato con Visual Studio SDK, in genere nella directory:
>
> *File di programma (x86) di C:*
>
> Per reimpostare la cache, immettere **CreateExpInstance /Reset**. Per ulteriori informazioni su **CreateExpInstance**, vedere [Utilità CreateExpInstance](../../extensibility/internals/createexpinstance-utility.md).

 Il primo elemento nell'elenco di elementi colorabili non viene mai fatto riferimento. Il primo elemento corrisponde a un indice [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] di elemento colorabile pari a 0 e fornisce sempre i colori e gli attributi di testo predefiniti per tale elemento. Il modo più semplice per gestire questo elemento senza riferimenti consiste nel fornire un elemento colorabile segnaposto nell'elenco come primo elemento.

## <a name="implement-custom-colorable-items"></a>Implementare elementi colorabili personalizzatiImplement custom colorable items

1. Definire gli elementi da colorare nella lingua, ad esempio Parola chiave, Operatore e Identificatore.

2. Creare un'enumerazione di questi elementi colorabili.

3. Associare i tipi di token restituiti da un parser o uno scanner ai valori enumerati.

    Ad esempio, i valori che rappresentano i tipi di token potrebbero essere gli stessi valori nell'enumerazione degli elementi colorabili personalizzati.

4. Nell'implementazione <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> del metodo <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> nell'oggetto, compilare l'elenco di attributi con i valori dell'enumerazione degli elementi colorabili personalizzati corrispondenti ai tipi di token restituiti dal parser o dallo scanner.

5. Nella stessa classe che <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> implementa l'interfaccia , implementare l'interfaccia <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems> e i relativi due metodi e <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetItemCount%2A> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A>.

6. Implementare l'interfaccia <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem>.

7. Se si desidera supportare valori di colore alti <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> o a 24 bit, implementare anche l'interfaccia.

8. Nell'oggetto servizio di linguaggio creare <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem> un elenco contenente gli oggetti, uno per ogni elemento colorabile che il parser o lo scanner può identificare.

    È possibile accedere a ogni elemento nell'elenco utilizzando il valore corrispondente dall'enumerazione degli elementi colorabili personalizzati. Utilizzare i valori di enumerazione come indice nell'elenco. Il primo elemento nell'elenco non è mai accessibile, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] perché corrisponde allo stile di testo predefinito che gestisce sempre se stesso. È possibile compensare questo inserendo un elemento colorabile segnaposto all'inizio dell'elenco.

9. Nell'implementazione <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetItemCount%2A> del metodo, restituire il numero di elementi nell'elenco di elementi colorabili personalizzati.

10. Nell'implementazione <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A> del metodo, restituire l'elemento colorabile richiesto dall'elenco.

    Per un esempio di <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem> implementazione delle interfacce e <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> , vedere <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem>.

## <a name="see-also"></a>Vedere anche
- [Modello di un servizio di linguaggio legacy](../../extensibility/internals/model-of-a-legacy-language-service.md)
- [Colorazione della sintassi negli editor personalizzati](../../extensibility/syntax-coloring-in-custom-editors.md)
- [Colorazione della sintassi in un servizio di linguaggio legacy](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)
- [Implementare la colorazione della sintassiImplement syntax coloring](../../extensibility/internals/implementing-syntax-coloring.md)
- [Procedura: Utilizzare elementi colorabili incorporatiHow to: Use built-in colorable items](../../extensibility/internals/how-to-use-built-in-colorable-items.md)

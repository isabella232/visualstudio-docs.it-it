---
title: Opzioni, Editor di testo, C#, IntelliSense | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.CSharp.Intellisense
- VS.ToolsOptionsPages.Text_Editor.Visual_JSharp.Intellisense
helpviewer_keywords:
- IntelliSense [J#], options
- underlines, wavy
- IntelliSense [C#], options
- IntelliSense [C#], wavy underlines
- wavy underlines
- Text Editor Options dialog box, IntelliSense
ms.assetid: 3466dedb-e5f4-424c-8dd8-e4941b2f4fc2
caps.latest.revision: 30
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 31c9909e5ea9364e806fdd2d7a39903bf1468abb
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49262171"
---
# <a name="options-text-editor-c-intellisense"></a>Opzioni, Editor di testo, C#, IntelliSense
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
Usare la pagina delle proprietà **IntelliSense** per modificare le impostazioni che hanno effetto sul comportamento di IntelliSense per Visual C#. È possibile accedere alla pagina delle proprietà **IntelliSense** facendo clic su **Opzioni** nel menu **Strumenti**, quindi su **C#** nella cartella **Editor di testo** e infine su **IntelliSense**.  
  
> [!NOTE]
>  Le finestre di dialogo e i comandi di menu visualizzati potrebbero essere diversi da quelli descritti nella Guida a seconda delle impostazioni attive o dell'edizione del programma. Per modificare le impostazioni, scegliere **Importa/Esporta impostazioni** dal menu **Strumenti** . Per altre informazioni, vedere [Personalizzazione delle impostazioni di sviluppo in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
 La pagina delle proprietà **IntelliSense** include le proprietà seguenti:  
  
## <a name="completion-lists"></a>Elenchi di completamento  
 **Mostra elenco di completamento dopo la digitazione di un carattere**  
 Quando questa opzione è selezionata, IntelliSense visualizza automaticamente l'elenco di completamento quando si inizia a digitare. Quando questa opzione non è selezionata, il completamento di IntelliSense è ancora disponibile tramite il menu **IntelliSense** o premendo CTRL+BARRA SPAZIATRICE.  
  
 **Inserisci parole chiave in elenchi di completamento**  
 Quando questa opzione è selezionata, IntelliSense aggiunge le parole chiave C#, ad esempio [class](http://msdn.microsoft.com/library/b95d8815-de18-4c3f-a8cc-a0a53bdf8690), all'elenco di completamento.  
  
 **Inserisci frammenti di codice in elenchi di completamento**  
 Quando questa opzione è selezionata, IntelliSense aggiunge gli alias per i frammenti di codice C# all'elenco di completamento. Se l'alias del frammento di codice corrisponde a una parola chiave, ad esempio [class](http://msdn.microsoft.com/library/b95d8815-de18-4c3f-a8cc-a0a53bdf8690), la parola chiave viene sostituita dal collegamento. Per altre informazioni, vedere [Frammenti di codice Visual C#](../../ide/visual-csharp-code-snippets.md).  
  
## <a name="selection-in-completion-lists"></a>Selezione negli elenchi di completamento  
 **Commit alla digitazione dei seguenti caratteri:**  
 Specifica tutti i caratteri che eseguono il completamento automatico IntelliSense per l'elemento selezionato nell'elenco di completamento dopo la digitazione.  
  
 **Commit alla pressione della barra spaziatrice**  
 Specifica di includere l'azione di pressione della barra spaziatrice per l'esecuzione del completamento automatico IntelliSense per l'elemento selezionato nell'elenco di completamento.  
  
 **Aggiungi nuova riga Invio alla fine della parola digitata**  
 Specifica che se si digitano tutti i caratteri di una voce dell'elenco di completamento e quindi si preme INVIO, viene creata automaticamente una nuova riga e il cursore si sposta nella nuova riga.  
  
 Ad esempio, se si digita `else` e quindi si preme INVIO, nell'editor verrà visualizzato quanto segue:  
  
 `else`  
  
 `|` (posizione del cursore)  
  
 Tuttavia, se si digita solo `el` e quindi si preme INVIO, nell'editor verrà visualizzato quanto segue:  
  
 `else|` (posizione del cursore)  
  
## <a name="intellisense-member-selection"></a>Selezione IntelliSense membri  
 **Preseleziona membri utilizzati più di recente**  
 Quando questa opzione è selezionata, IntelliSense preseleziona i membri recentemente selezionati nella casella popup Elenca membri per il completamento automatico del nome dell'oggetto durante la sessione corrente nell'ambiente di sviluppo integrato (IDE). La cronologia dei membri utilizzati più di recente viene cancellata tra ogni sessione nell'ambiente di sviluppo integrato. Per altre informazioni, vedere [IntelliSense per i membri usati di recente](../../misc/intellisense-for-most-recently-used-members.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Generale, Ambiente, finestra di dialogo Opzioni](../../ide/reference/general-environment-options-dialog-box.md)   
 [Commenti relativi alla documentazione XML](http://msdn.microsoft.com/library/803b7f7b-7428-4725-b5db-9a6cff273199)   
 [Utilizzo di IntelliSense](../../ide/using-intellisense.md)




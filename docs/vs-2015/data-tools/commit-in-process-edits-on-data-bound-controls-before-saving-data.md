---
title: Eseguire il commit delle modifiche in corso nei controlli con associazione a dati prima del salvataggio dei dati | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- commiting edited records
- data-bound controls, in-process edits
- DataBinding class, commiting edited records
- hierarchical update, commiting edited records
- BindingSource class, commiting edited records
- EndEdit method
ms.assetid: 61af4798-eef7-468c-b229-5e1497febb2f
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: bd56f9acfce7933d0bc89e7e86eb8083b9b1f867
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47525280"
---
# <a name="commit-in-process-edits-on-data-bound-controls-before-saving-data"></a>Eseguire il commit delle modifiche in corso nei controlli con associazione a dati prima del salvataggio dei dati
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [eseguire il Commit delle modifiche in corso nei controlli con associazione a dati prima di salvare dati](https://docs.microsoft.com/visualstudio/data-tools/commit-in-process-edits-on-data-bound-controls-before-saving-data).  
  
  
Quando si modificano i valori nei controlli con associazione a dati, è necessario spostarsi dal record corrente per eseguire il commit il valore aggiornato dell'origine dati sottostante che è associato il controllo. Quando si trascinano elementi dal [finestra Origini dati](http://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992) in un form, il primo elemento che elimina genera il codice nelle **salvare** dell'evento click del pulsante di <xref:System.Windows.Forms.BindingNavigator>. Questo codice chiama il <xref:System.Windows.Forms.BindingSource.EndEdit%2A> metodo di <xref:System.Windows.Forms.BindingSource>. Pertanto, la chiamata per il <xref:System.Windows.Forms.BindingSource.EndEdit%2A> metodo viene generato solo per i primi <xref:System.Windows.Forms.BindingSource> che viene aggiunto al form.  
  
 Il <xref:System.Windows.Forms.BindingSource.EndEdit%2A> chiamata esegue il commit di tutte le modifiche in corso, in tutti i controlli con associazione a dati che si stanno modificando. Di conseguenza, se un controllo con associazione a dati ha lo stato attivo e si sceglie la **salvare** button, tutte le modifiche in sospeso in tale controllo viene eseguito il commit prima del salvataggio effettivo (il `TableAdapterManager.UpdateAll` (metodo)).  
  
 È possibile configurare l'applicazione per eseguire automaticamente il commit delle modifiche, anche se un utente tenta di salvare i dati senza eseguire il commit delle modifiche, come parte del salvataggio processo.  
  
> [!NOTE]
>  La finestra di progettazione aggiunge il `BindingSource.EndEdit` codice solo per il primo elemento rilasciato in un form. Pertanto, è necessario aggiungere una riga di codice per chiamare il <xref:System.Windows.Forms.BindingSource.EndEdit%2A> per ogni metodo <xref:System.Windows.Forms.BindingSource> nel form. È possibile aggiungere manualmente una riga di codice per chiamare il <xref:System.Windows.Forms.BindingSource.EndEdit%2A> per ogni metodo <xref:System.Windows.Forms.BindingSource>. In alternativa, è possibile aggiungere il `EndEditOnAllBindingSources` metodo al form e chiamarlo prima di eseguire un salvataggio.  
  
 Il codice seguente usa un' [LINQ (Language-Integrated Query)](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d) query per eseguire l'iterazione di tutti <xref:System.Windows.Forms.BindingSource> componenti e chiamare il <xref:System.Windows.Forms.BindingSource.EndEdit%2A> metodo per ogni <xref:System.Windows.Forms.BindingSource> in un form.  
  
## <a name="to-call-endedit-for-all-bindingsource-components-on-a-form"></a>Per chiamare EndEdit per tutti i componenti di BindingSource in un form  
  
1.  Aggiungere il codice seguente al form che contiene il <xref:System.Windows.Forms.BindingSource> componenti.  
  
     [!code-csharp[VSProDataOrcasEndEditOnAll#1](../snippets/csharp/VS_Snippets_VBCSharp/VSProDataOrcasEndEditOnAll/CS/Form1.cs#1)]
     [!code-vb[VSProDataOrcasEndEditOnAll#1](../snippets/visualbasic/VS_Snippets_VBCSharp/VSProDataOrcasEndEditOnAll/VB/Form1.vb#1)]  
  
2.  Aggiungere la seguente riga di codice immediatamente prima delle chiamate per salvare i dati del modulo (il `TableAdapterManager.UpdateAll()` (metodo)):  
  
     [!code-csharp[VSProDataOrcasEndEditOnAll#2](../snippets/csharp/VS_Snippets_VBCSharp/VSProDataOrcasEndEditOnAll/CS/Form1.cs#2)]
     [!code-vb[VSProDataOrcasEndEditOnAll#2](../snippets/visualbasic/VS_Snippets_VBCSharp/VSProDataOrcasEndEditOnAll/VB/Form1.vb#2)]  
  
## <a name="see-also"></a>Vedere anche  
 [Associazione di controlli Windows Form ai dati in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Aggiornamento gerarchico](../data-tools/hierarchical-update.md)


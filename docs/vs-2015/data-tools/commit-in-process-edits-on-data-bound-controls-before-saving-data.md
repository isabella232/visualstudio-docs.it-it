---
title: Eseguire il commit delle modifiche in-process sui controlli con associazione a dati prima di salvare i dati | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- committing edited records
- data-bound controls, in-process edits
- DataBinding class, committing edited records
- hierarchical update, committing edited records
- BindingSource class, committing edited records
- EndEdit method
ms.assetid: 61af4798-eef7-468c-b229-5e1497febb2f
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3867b91a8b417b5670514b66aaf93fdab4e9618c
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72662457"
---
# <a name="commit-in-process-edits-on-data-bound-controls-before-saving-data"></a>Eseguire il commit delle modifiche in corso nei controlli con associazione a dati prima del salvataggio dei dati
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Quando si modificano i valori nei controlli associati a dati, gli utenti devono passare al record corrente per eseguire il commit del valore aggiornato nell'origine dati sottostante a cui è associato il controllo. Quando si trascinano elementi dalla [finestra Origini dati](https://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992) in un form, il primo elemento eliminato genera il codice nell'evento click del pulsante **Salva** del <xref:System.Windows.Forms.BindingNavigator>. Questo codice chiama il metodo <xref:System.Windows.Forms.BindingSource.EndEdit%2A> della <xref:System.Windows.Forms.BindingSource>. La chiamata al metodo <xref:System.Windows.Forms.BindingSource.EndEdit%2A> viene pertanto generata solo per la prima <xref:System.Windows.Forms.BindingSource> aggiunta al modulo.

 La chiamata di <xref:System.Windows.Forms.BindingSource.EndEdit%2A> esegue il commit di tutte le modifiche in corso nei controlli associati a dati che si stanno modificando. Pertanto, se un controllo associato a dati ha lo stato attivo e si fa clic sul pulsante **Salva**, prima del salvataggio effettivo verrà eseguito il commit di tutte le modifiche in sospeso nel controllo (metodo `TableAdapterManager.UpdateAll`).

 È possibile configurare l'applicazione in modo da eseguire automaticamente il commit delle modifiche, anche se un utente tenta di salvare i dati senza eseguire il commit delle modifiche, come parte del processo di salvataggio.

> [!NOTE]
> La finestra di progettazione aggiunge il codice `BindingSource.EndEdit` solo per il primo elemento rilasciato in un form. Pertanto, è necessario aggiungere una riga di codice per chiamare il metodo <xref:System.Windows.Forms.BindingSource.EndEdit%2A> per ogni <xref:System.Windows.Forms.BindingSource> nel form. È possibile aggiungere manualmente una riga di codice per chiamare il metodo <xref:System.Windows.Forms.BindingSource.EndEdit%2A> per ogni <xref:System.Windows.Forms.BindingSource>. In alternativa, è possibile aggiungere il metodo `EndEditOnAllBindingSources` al form e chiamarlo prima di eseguire un salvataggio.

 Il codice seguente usa una query [LINQ (Language-Integrated Query)](https://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d) per eseguire l'iterazione di tutti i componenti <xref:System.Windows.Forms.BindingSource> e chiamare il metodo <xref:System.Windows.Forms.BindingSource.EndEdit%2A> per ogni <xref:System.Windows.Forms.BindingSource> in un form.

## <a name="to-call-endedit-for-all-bindingsource-components-on-a-form"></a>Per chiamare EndEdit per tutti i componenti BindingSource in un form

1. Aggiungere il codice seguente al form che contiene i componenti <xref:System.Windows.Forms.BindingSource>.

     [!code-csharp[VSProDataOrcasEndEditOnAll#1](../snippets/csharp/VS_Snippets_VBCSharp/VSProDataOrcasEndEditOnAll/CS/Form1.cs#1)]
     [!code-vb[VSProDataOrcasEndEditOnAll#1](../snippets/visualbasic/VS_Snippets_VBCSharp/VSProDataOrcasEndEditOnAll/VB/Form1.vb#1)]

2. Aggiungere la riga di codice seguente immediatamente prima di tutte le chiamate per salvare i dati del form (il metodo `TableAdapterManager.UpdateAll()`):

     [!code-csharp[VSProDataOrcasEndEditOnAll#2](../snippets/csharp/VS_Snippets_VBCSharp/VSProDataOrcasEndEditOnAll/CS/Form1.cs#2)]
     [!code-vb[VSProDataOrcasEndEditOnAll#2](../snippets/visualbasic/VS_Snippets_VBCSharp/VSProDataOrcasEndEditOnAll/VB/Form1.vb#2)]

## <a name="see-also"></a>Vedere anche
 [Associare controlli Windows Forms ai dati nell'](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md) [aggiornamento gerarchico](../data-tools/hierarchical-update.md) di Visual Studio

---
title: Commit delle modifiche in-process sui controlli con associazione a dati prima del salvataggio
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- committing edited records
- data-bound controls, in-process edits
- DataBinding class, committing edited records
- hierarchical update, committing edited records
- BindingSource class, committing edited records
- EndEdit method
ms.assetid: 61af4798-eef7-468c-b229-5e1497febb2f
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 129f8e03ca982dc1e028dc23a9e342b5793e39cf
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72648680"
---
# <a name="commit-in-process-edits-on-data-bound-controls-before-saving-data"></a>Eseguire il commit delle modifiche in corso nei controlli con associazione a dati prima del salvataggio dei dati

Quando si modificano i valori nei controlli associati a dati, gli utenti devono passare al record corrente per eseguire il commit del valore aggiornato nell'origine dati sottostante a cui è associato il controllo. Quando si trascinano elementi dalla [finestra Origini dati](add-new-data-sources.md) in un form, il primo elemento eliminato genera il codice nell'evento click del pulsante **Salva** del <xref:System.Windows.Forms.BindingNavigator>. Questo codice chiama il metodo <xref:System.Windows.Forms.BindingSource.EndEdit%2A> della <xref:System.Windows.Forms.BindingSource>. La chiamata al metodo <xref:System.Windows.Forms.BindingSource.EndEdit%2A> viene pertanto generata solo per la prima <xref:System.Windows.Forms.BindingSource> aggiunta al modulo.

La chiamata di <xref:System.Windows.Forms.BindingSource.EndEdit%2A> esegue il commit di tutte le modifiche in corso nei controlli associati a dati che si stanno modificando. Pertanto, se un controllo associato a dati ha lo stato attivo e si fa clic sul pulsante **Salva**, prima del salvataggio effettivo verrà eseguito il commit di tutte le modifiche in sospeso nel controllo (metodo `TableAdapterManager.UpdateAll`).

È possibile configurare l'applicazione in modo da eseguire automaticamente il commit delle modifiche, anche se un utente tenta di salvare i dati senza eseguire il commit delle modifiche, come parte del processo di salvataggio.

> [!NOTE]
> La finestra di progettazione aggiunge il codice `BindingSource.EndEdit` solo per il primo elemento rilasciato in un form. Pertanto, è necessario aggiungere una riga di codice per chiamare il metodo <xref:System.Windows.Forms.BindingSource.EndEdit%2A> per ogni <xref:System.Windows.Forms.BindingSource> nel form. È possibile aggiungere manualmente una riga di codice per chiamare il metodo <xref:System.Windows.Forms.BindingSource.EndEdit%2A> per ogni <xref:System.Windows.Forms.BindingSource>. In alternativa, è possibile aggiungere il metodo `EndEditOnAllBindingSources` al form e chiamarlo prima di eseguire un salvataggio.

Il codice seguente usa una query [LINQ (Language-Integrated Query)](/dotnet/csharp/linq/) per eseguire l'iterazione di tutti i componenti <xref:System.Windows.Forms.BindingSource> e chiamare il metodo <xref:System.Windows.Forms.BindingSource.EndEdit%2A> per ogni <xref:System.Windows.Forms.BindingSource> in un form.

## <a name="to-call-endedit-for-all-bindingsource-components-on-a-form"></a>Per chiamare EndEdit per tutti i componenti BindingSource in un form

1. Aggiungere il codice seguente al form che contiene i componenti <xref:System.Windows.Forms.BindingSource>.

     [!code-csharp[VSProDataOrcasEndEditOnAll#1](../data-tools/codesnippet/CSharp/commit-in-process-edits-on-data-bound-controls-before-saving-data_1.cs)]
     [!code-vb[VSProDataOrcasEndEditOnAll#1](../data-tools/codesnippet/VisualBasic/commit-in-process-edits-on-data-bound-controls-before-saving-data_1.vb)]

2. Aggiungere la riga di codice seguente immediatamente prima di tutte le chiamate per salvare i dati del form (il metodo `TableAdapterManager.UpdateAll()`):

     [!code-csharp[VSProDataOrcasEndEditOnAll#2](../data-tools/codesnippet/CSharp/commit-in-process-edits-on-data-bound-controls-before-saving-data_2.cs)]
     [!code-vb[VSProDataOrcasEndEditOnAll#2](../data-tools/codesnippet/VisualBasic/commit-in-process-edits-on-data-bound-controls-before-saving-data_2.vb)]

## <a name="see-also"></a>Vedere anche

- [Associare controlli Windows Form ai dati in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
- [Aggiornamento gerarchico](../data-tools/hierarchical-update.md)
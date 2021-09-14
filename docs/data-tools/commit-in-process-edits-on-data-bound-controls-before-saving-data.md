---
title: Modifiche di cui non è stato eseguito ilcommitted
description: Eseguire il commit delle modifiche in-process nei controlli form associati Windows dati prima di salvare i dati. Chiamare EndEdit per tutti i componenti BindingSource in un form.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
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
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 9e69734b43a0c959a724ee9116f919597c14002d
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126631542"
---
# <a name="commit-in-process-edits-on-data-bound-controls-before-saving-data"></a>Eseguire il commit delle modifiche in corso nei controlli con associazione a dati prima del salvataggio dei dati

Quando si modificano i valori nei controlli associati a dati, gli utenti devono disconnettersi dal record corrente per eseguire il commit del valore aggiornato nell'origine dati sottostante a cui è associato il controllo. Quando si trascinano elementi dalla [finestra Origini dati](add-new-data-sources.md) in un form,  il primo elemento che si rilascia genera codice nell'evento Click del pulsante Salva di <xref:System.Windows.Forms.BindingNavigator> . Questo codice chiama il <xref:System.Windows.Forms.BindingSource.EndEdit%2A> metodo dell'oggetto <xref:System.Windows.Forms.BindingSource> . Pertanto, la chiamata al <xref:System.Windows.Forms.BindingSource.EndEdit%2A> metodo viene generata solo per il primo che viene aggiunto al <xref:System.Windows.Forms.BindingSource> form.

La chiamata di <xref:System.Windows.Forms.BindingSource.EndEdit%2A> esegue il commit di tutte le modifiche in corso nei controlli associati a dati che si stanno modificando. Pertanto, se un controllo associato a dati ha lo stato attivo e si fa clic sul pulsante **Salva**, prima del salvataggio effettivo verrà eseguito il commit di tutte le modifiche in sospeso nel controllo (metodo `TableAdapterManager.UpdateAll`).

È possibile configurare l'applicazione per il commit automatico delle modifiche, anche se un utente tenta di salvare i dati senza eseguire il commit delle modifiche, come parte del processo di salvataggio.

> [!NOTE]
> La finestra di progettazione `BindingSource.EndEdit` aggiunge il codice solo per il primo elemento rilasciato in un form. Pertanto, è necessario aggiungere una riga di codice per chiamare il <xref:System.Windows.Forms.BindingSource.EndEdit%2A> metodo per ogni nel <xref:System.Windows.Forms.BindingSource> form. È possibile aggiungere manualmente una riga di codice per chiamare il <xref:System.Windows.Forms.BindingSource.EndEdit%2A> metodo per ogni <xref:System.Windows.Forms.BindingSource> . In alternativa, è possibile aggiungere `EndEditOnAllBindingSources` il metodo al form e chiamarlo prima di eseguire un salvataggio.

Il codice seguente usa una query [LINQ (Language-Integrated Query)](/dotnet/csharp/linq/) per eseguire l'iterazione di tutti i componenti e chiamare il metodo <xref:System.Windows.Forms.BindingSource> per ognuno di essi in un <xref:System.Windows.Forms.BindingSource.EndEdit%2A> <xref:System.Windows.Forms.BindingSource> form.

## <a name="to-call-endedit-for-all-bindingsource-components-on-a-form"></a>Per chiamare EndEdit per tutti i componenti BindingSource in un form

1. Aggiungere il codice seguente al form che contiene i <xref:System.Windows.Forms.BindingSource> componenti.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VSProDataOrcasEndEditOnAll/CS/Form1.cs" id="Snippet1":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VSProDataOrcasEndEditOnAll/VB/Form1.vb" id="Snippet1":::

2. Aggiungere la riga di codice seguente immediatamente prima di qualsiasi chiamata a per salvare i dati del form (il `TableAdapterManager.UpdateAll()` metodo ):

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VSProDataOrcasEndEditOnAll/CS/Form1.cs" id="Snippet2":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VSProDataOrcasEndEditOnAll/VB/Form1.vb" id="Snippet2":::

## <a name="see-also"></a>Vedi anche

- [Associare controlli Windows Form ai dati in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
- [Aggiornamento gerarchico](../data-tools/hierarchical-update.md)

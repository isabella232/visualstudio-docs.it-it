---
title: 'Procedura: creare metodi DataContext mappati a stored procedure e funzioni (O-R Designer) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: e7ca32f1-50b3-48af-ad92-ceafd749296a
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 70053b74a4dd2ad569e1e8195f4c9b2e7b214440
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72665970"
---
# <a name="how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-or-designer"></a>Procedura: Creare metodi DataContext mappati a stored procedure e funzioni (Object Relational Designer)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Le stored procedure e le funzioni possono essere aggiunte alla [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] come <xref:System.Data.Linq.DataContext> metodi. La chiamata al metodo e il passaggio dei parametri obbligatori comportano l'esecuzione della stored procedure o funzione nel database e la restituzione dei dati nel tipo restituito del metodo <xref:System.Data.Linq.DataContext>. Per informazioni dettagliate sui metodi di <xref:System.Data.Linq.DataContext>, vedere [metodi DataContext (O/R Designer)](../data-tools/datacontext-methods-o-r-designer.md).

> [!NOTE]
> Le stored procedure possono essere usate anche per eseguire l'override del comportamento in fase di esecuzione [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] predefinito che esegue i comandi di inserimento, aggiornamento ed eliminazione durante il salvataggio delle modifiche dalle classi di entità in un database. Per altre informazioni, vedere [procedura: assegnare stored procedure per eseguire aggiornamenti, inserimenti ed eliminazioni (O/R Designer)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md).

## <a name="creating-datacontext-methods"></a>Creazione di metodi DataContext
 È possibile creare <xref:System.Data.Linq.DataContext> metodi trascinando le stored procedure o le funzioni da **Esplora server/Esplora database** nel [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)].

> [!NOTE]
> Il tipo restituito del metodo <xref:System.Data.Linq.DataContext> generato varia a seconda della posizione in cui si rilascia la stored procedure o funzione in [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]. Il rilascio degli elementi direttamente in una classe di entità esistente crea un metodo <xref:System.Data.Linq.DataContext> con il tipo restituito della classe di entità, mentre il rilascio degli elementi in un'area vuota di [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] crea un metodo <xref:System.Data.Linq.DataContext> che restituisce un tipo generato automaticamente. È possibile modificare il tipo restituito di un metodo di <xref:System.Data.Linq.DataContext> dopo averlo aggiunto al riquadro dei metodi. Per controllare o modificare il tipo restituito di un metodo <xref:System.Data.Linq.DataContext>, selezionarlo e controllare la proprietà **Return Type** nella finestra **Proprietà**. Per altre informazioni, vedere [procedura: modificare il tipo restituito di un metodo DataContext (O/R Designer)](../data-tools/how-to-change-the-return-type-of-a-datacontext-method-o-r-designer.md).

 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]

#### <a name="to-create-datacontext-methods-that-return-automatically-generated-types"></a>Per creare metodi DataContext che restituiscono tipi generati automaticamente

1. In **Esplora server** /**Esplora database**espandere il nodo **stored procedure** del database che si sta utilizzando.

2. Individuare la stored procedure desiderata e trascinarla in un'area vuota di [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)].

     Il metodo <xref:System.Data.Linq.DataContext> viene creato con un tipo restituito generato automaticamente e viene visualizzato nel riquadro **Metodi**.

#### <a name="to-create-datacontext-methods-that-have-the-return-type-of-an-entity-class"></a>Per creare metodi DataContext con il tipo restituito di una classe di entità

1. In **Esplora server** /**Esplora database**espandere il nodo **stored procedure** del database che si sta utilizzando.

2. Individuare la stored procedure desiderata e trascinarla in una classe di entità esistente di [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)].

     Il metodo <xref:System.Data.Linq.DataContext> viene creato con il tipo restituito della classe di entità selezionata e viene visualizzato nel riquadro **Metodi**.

> [!NOTE]
> Per informazioni su come modificare il tipo restituito predefinito esistente <xref:System.Data.Linq.DataContext> metodi, vedere [come: Modificare il tipo restituito di un metodo DataContext (O/R Designer)](../data-tools/how-to-change-the-return-type-of-a-datacontext-method-o-r-designer.md).

## <a name="see-also"></a>Vedere anche
 [Strumenti di LINQ to SQL in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md) [metodi DataContext (o/r designer)](../data-tools/datacontext-methods-o-r-designer.md) [procedura dettagliata: creazione di classi LINQ to SQL (o-r designer)](https://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233) [LINQ to SQL](https://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655) [Introduzione a LINQ in Visual Basic](https://msdn.microsoft.com/library/3047d86e-0d49-40e2-928b-dc02e46c7984) [procedura: scrivere query LINQ in C#](https://msdn.microsoft.com/library/45e47fcc-cfa1-4b72-b161-d038ae87bd23)

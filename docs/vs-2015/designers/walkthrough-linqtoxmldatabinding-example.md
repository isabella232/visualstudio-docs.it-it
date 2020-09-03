---
title: 'Procedura dettagliata: Esempio LinqToXmlDataBinding | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: aedf42e8-896c-48fa-88df-7f7c9536aa69
caps.latest.revision: 4
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 0e97d612e19f64110f3090029dcff82acbad8e87
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "72663977"
---
# <a name="walkthrough-linqtoxmldatabinding-example"></a>Procedura dettagliata: Esempio LinqToXmlDataBinding
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In questa procedura dettagliata viene descritto l'esempio LinqToXmlDataBinding e vengono illustrato parte del contenuto più interessante dei due file di origine principali, ovvero L2DBForm.xaml e L2DBForm.xaml.cs.

## <a name="prerequisites"></a>Prerequisiti
 Prima di leggere questa procedura dettagliata, è consigliabile compilare ed eseguire il programma LinqToXmlDataBinding come descritto in [procedura: compilare ed eseguire l'esempio di LinqToXmlDataBinding](../designers/how-to-build-and-run-the-linqtoxmldatabinding-example.md).

## <a name="remarks"></a>Osservazioni
 LinqToXmlDataBinding è un'applicazione di Windows Presentation Foundation (WPF) composta da file di origine C# e XAML. Contiene un documento XML incorporato che definisce un elenco di libri e consente all'utente di visualizzare, aggiungere, eliminare e modificare queste voci. È costituita dai due file di origine principali seguenti:

- L2DBForm.xaml: contiene il codice della dichiarazione XAML per l'interfaccia utente della finestra principale. Include inoltre una sezione di risorse della finestra in cui vengono definiti un provider di dati e un documento XML incorporato per gli elenchi di libri.

- L2DBForm.xaml.cs: contiene i metodi di inizializzazione e gestione eventi associati all'interfaccia utente.

  La finestra principale è divisa nelle quattro sezioni di interfaccia utente verticali descritte di seguito:

- **XML**: visualizza l'origine XML non elaborata dell'elenco di libri incorporato.

- **Book List**: visualizza le voci relative ai libri come testo standard e consente all'utente di selezionare ed eliminare singole voci.

- **Edit Selected Book**: consente all'utente di modificare i valori associati alla voce attualmente selezionata.

- **Add New Book**: consente di creare una nuova voce in base ai valori immessi dall'utente.

## <a name="in-this-section"></a>Contenuto della sezione

|Argomento|Descrizione|
|-----------|-----------------|
|[Codice sorgente di L2DBForm. XAML](../designers/l2dbform-xaml-source-code.md)|Vengono forniti il contenuto e la descrizione del codice XAML del file L2DBForm.xaml.|
|[Codice sorgente L2DBForm.xaml.cs](../designers/l2dbform-xaml-cs-source-code.md)|Vengono forniti il contenuto e la descrizione del codice sorgente C# del file L2DBForm.xaml.cs.|

## <a name="see-also"></a>Vedere anche
 [Data Binding WPF con LINQ to XML esempio](../designers/wpf-data-binding-using-linq-to-xml-example.md) [procedura: compilare ed eseguire l'esempio LinqToXmlDataBinding](../designers/how-to-build-and-run-the-linqtoxmldatabinding-example.md)

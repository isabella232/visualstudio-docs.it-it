---
title: 'Procedura dettagliata: Esempio LinqToXmlDataBinding | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: aedf42e8-896c-48fa-88df-7f7c9536aa69
caps.latest.revision: 4
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 723f6b121d844fa5a8e504e8106fdcfc6c58f012
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47540686"
---
# <a name="walkthrough-linqtoxmldatabinding-example"></a>Procedura dettagliata: Esempio LinqToXmlDataBinding
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [procedura dettagliata: esempio LinqToXmlDataBinding](https://docs.microsoft.com/visualstudio/designers/walkthrough-linqtoxmldatabinding-example).  
  
In questa procedura dettagliata viene descritto l'esempio LinqToXmlDataBinding e vengono illustrato parte del contenuto più interessante dei due file di origine principali, ovvero L2DBForm.xaml e L2DBForm.xaml.cs.  
  
## <a name="prerequisites"></a>Prerequisiti  
 Prima di leggere questa procedura dettagliata, è consigliabile compilare ed eseguire l'applicazione LinqToXmlDataBinding come descritto in [Procedura: Compilare ed eseguire l'esempio LinqToXmlDataBinding](../designers/how-to-build-and-run-the-linqtoxmldatabinding-example.md).  
  
## <a name="remarks"></a>Note  
 LinqToXmlDataBinding è un'applicazione di Windows Presentation Foundation (WPF) composta da file di origine C# e XAML. Contiene un documento XML incorporato che definisce un elenco di libri e consente all'utente di visualizzare, aggiungere, eliminare e modificare queste voci. È costituita dai due file di origine principali seguenti:  
  
-   L2DBForm.xaml: contiene il codice della dichiarazione XAML per l'interfaccia utente della finestra principale. Include inoltre una sezione di risorse della finestra in cui vengono definiti un provider di dati e un documento XML incorporato per gli elenchi di libri.  
  
-   L2DBForm.xaml.cs: contiene i metodi di inizializzazione e gestione eventi associati all'interfaccia utente.  
  
 La finestra principale è divisa nelle quattro sezioni di interfaccia utente verticali descritte di seguito:  
  
-   **XML**: visualizza l'origine XML non elaborata dell'elenco di libri incorporato.  
  
-   **Book List**: visualizza le voci relative ai libri come testo standard e consente all'utente di selezionare ed eliminare singole voci.  
  
-   **Edit Selected Book**: consente all'utente di modificare i valori associati alla voce attualmente selezionata.  
  
-   **Add New Book**: consente di creare una nuova voce in base ai valori immessi dall'utente.  
  
## <a name="in-this-section"></a>In questa sezione  
  
|Argomento|Descrizione|  
|-----------|-----------------|  
|[Codice sorgente di L2DBForm.xaml](../designers/l2dbform-xaml-source-code.md)|Vengono forniti il contenuto e la descrizione del codice XAML del file L2DBForm.xaml.|  
|[Codice sorgente di L2DBForm.xaml.cs](../designers/l2dbform-xaml-cs-source-code.md)|Vengono forniti il contenuto e la descrizione del codice sorgente C# del file L2DBForm.xaml.cs.|  
  
## <a name="see-also"></a>Vedere anche  
 [Esempio di associazione dati di WPF con LINQ to XML](../designers/wpf-data-binding-using-linq-to-xml-example.md)   
 [Procedura: Compilare ed eseguire l'esempio LinqToXmlDataBinding](../designers/how-to-build-and-run-the-linqtoxmldatabinding-example.md)




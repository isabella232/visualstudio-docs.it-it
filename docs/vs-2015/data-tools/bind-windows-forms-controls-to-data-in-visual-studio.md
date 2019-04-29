---
title: Associare controlli Windows Form ai dati
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
- data [Windows Forms], data sources
- Windows Forms, data binding
- Windows Forms, displaying data
- displaying data on forms
- forms, displaying data
- data sources, displaying data
- displaying data, Windows Forms
- data [Windows Forms], displaying
ms.assetid: 243338ef-41af-4cc5-aff7-1e830236f0ec
caps.latest.revision: 40
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 0f2bd51570c8ad1976b6fc9eb5674177f9342833
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62556608"
---
# <a name="bind-windows-forms-controls-to-data-in-visual-studio"></a>Associare controlli Windows Form ai dati in Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

È possibile visualizzare i dati agli utenti dell'applicazione mediante l'associazione dati a un Windows Form. Per creare questi controlli con associazione a dati, è possibile trascinare elementi dal **Zdroje dat** finestra in Progettazione Windows Form in Visual Studio. Questo argomento descrive alcune delle più comuni attività, strumenti e le classi coinvolte nella creazione di applicazioni di Windows Form con associazione a dati.

 ![Operazione di trascinamento Zdroj](../data-tools/media/raddata-data-source-drag-operation.png "raddata Zdroj dat operazione di trascinamento")

 Per informazioni generali su come creare controlli associati a dati in Visual Studio, vedere [associare controlli ai dati in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md). Per altre informazioni sul data binding in Windows Form, vedere [Data Binding in Windows Form](http://msdn.microsoft.com/library/c3826d8e-ea25-4ad4-a669-45bfb19192aa).

## <a name="in-this-section"></a>Contenuto della sezione

- [Associare controlli Windows Form ai dati](../data-tools/bind-windows-forms-controls-to-data.md)

- [Eseguire il commit delle modifiche in corso nei controlli con associazione a dati prima del salvataggio dei dati](../data-tools/commit-in-process-edits-on-data-bound-controls-before-saving-data.md)

- [Creare tabelle di ricerca nelle applicazioni Windows Forms](../data-tools/create-lookup-tables-in-windows-forms-applications.md)

- [Creare un Windows Form per la ricerca di dati](../data-tools/create-a-windows-form-to-search-data.md)

- [Creare un controllo utente Windows Form che supporta il data binding semplice](../data-tools/create-a-windows-forms-user-control-that-supports-simple-data-binding.md)

- [Creare un controllo utente Windows Form che supporta il data binding complesso](../data-tools/create-a-windows-forms-user-control-that-supports-complex-data-binding.md)

- [Creare un controllo utente Windows Form che supporta il data binding di ricerca](../data-tools/create-a-windows-forms-user-control-that-supports-lookup-data-binding.md)

- [Passare dati da un form all'altro](../data-tools/pass-data-between-forms.md)

## <a name="bindingsource-component"></a>BindingSource (componente)
 Il componente <xref:System.Windows.Forms.BindingSource> ha due scopi. In primo luogo, fornisce un livello di astrazione quando i controlli nel form di associazione a dati. I controlli nel form sono associati ai <xref:System.Windows.Forms.BindingSource> componente (anziché viene associato direttamente a un'origine dati).

 In secondo luogo, è possibile gestire una raccolta di oggetti. Aggiunta di un tipo per il <xref:System.Windows.Forms.BindingSource> crea un elenco di quel tipo.

 Per altre informazioni sul <xref:System.Windows.Forms.BindingSource> componente, vedere:

- [Componente BindingSource](http://msdn.microsoft.com/library/3e2faf4c-f5b8-4fa6-9fbc-f59c37ec2fb9)

- [Cenni preliminari sul componente BindingSource](http://msdn.microsoft.com/library/be838caf-fcb0-4b68-827f-58b2c04b747f)

- [Architettura del componente BindingSource](http://msdn.microsoft.com/library/7bc69c90-8a11-48b1-9336-3adab5b41591)

## <a name="bindingnavigator-control"></a>BindingNavigator (controllo)
 Questo componente fornisce un'interfaccia utente per l'esplorazione dei dati visualizzati in un'applicazione Windows. Per altre informazioni, vedere [Controllo BindingNavigator](http://msdn.microsoft.com/library/18c1e2a5-9834-40d3-9b2e-2b545e4e769e).

## <a name="datagridview-control"></a>DataGridView (controllo)
 Per visualizzare e modificare dati tabulari forniti da molti tipi diversi di origini dati, usare il <xref:System.Windows.Forms.DataGridView> controllo. È possibile associare dati a un <xref:System.Windows.Forms.DataGridView> utilizzando il <xref:System.Windows.Forms.DataGridView.DataSource%2A> proprietà. Per altre informazioni, vedere [Cenni preliminari sul controllo DataGridView](http://msdn.microsoft.com/library/0a45c661-89dc-4390-9cc6-c47eee501488).

## <a name="see-also"></a>Vedere anche
 [Associare controlli ai dati in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)

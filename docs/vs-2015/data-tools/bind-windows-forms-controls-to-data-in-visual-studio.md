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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 8a03f4df57b216fa68e5ac24df80b67917aa3e3f
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72672981"
---
# <a name="bind-windows-forms-controls-to-data-in-visual-studio"></a>Associare controlli Windows Form ai dati in Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

È possibile visualizzare i dati per gli utenti dell'applicazione associando i dati a Windows Forms. Per creare questi controlli associati a dati, è possibile trascinare gli elementi dalla finestra **origini dati** nel Progettazione Windows Form in Visual Studio. In questo argomento vengono descritte alcune delle attività, degli strumenti e delle classi più comuni per la creazione di applicazioni di Windows Forms con associazione a dati.

 ![Operazione di trascinamento dell'origine dati](../data-tools/media/raddata-data-source-drag-operation.png "operazione di trascinamento dell'origine dati raddata")

 Per informazioni generali su come creare controlli associati a dati in Visual Studio, vedere [associare i controlli ai dati in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md). Per ulteriori informazioni su data binding in Windows Forms, vedere [Windows Forms Data Binding](https://msdn.microsoft.com/library/c3826d8e-ea25-4ad4-a669-45bfb19192aa).

## <a name="in-this-section"></a>In questa sezione

- [Associare controlli Windows Form ai dati](../data-tools/bind-windows-forms-controls-to-data.md)

- [Eseguire il commit delle modifiche in corso nei controlli con associazione a dati prima del salvataggio dei dati](../data-tools/commit-in-process-edits-on-data-bound-controls-before-saving-data.md)

- [Creare tabelle di ricerca nelle applicazioni Windows Forms](../data-tools/create-lookup-tables-in-windows-forms-applications.md)

- [Creare un Windows Form per la ricerca di dati](../data-tools/create-a-windows-form-to-search-data.md)

- [Creare un controllo utente Windows Form che supporta il data binding semplice](../data-tools/create-a-windows-forms-user-control-that-supports-simple-data-binding.md)

- [Creare un controllo utente Windows Form che supporta il data binding complesso](../data-tools/create-a-windows-forms-user-control-that-supports-complex-data-binding.md)

- [Creare un controllo utente Windows Form che supporta il data binding di ricerca](../data-tools/create-a-windows-forms-user-control-that-supports-lookup-data-binding.md)

- [Passare dati da un form all'altro](../data-tools/pass-data-between-forms.md)

## <a name="bindingsource-component"></a>BindingSource (componente)
 Il componente <xref:System.Windows.Forms.BindingSource> ha due scopi. In primo luogo, fornisce un livello di astrazione durante l'associazione dei controlli nel form ai dati. I controlli nel form sono associati al componente <xref:System.Windows.Forms.BindingSource>, anziché essere associati direttamente a un'origine dati.

 In secondo luogo, è in grado di gestire una raccolta di oggetti. Se si aggiunge un tipo all'<xref:System.Windows.Forms.BindingSource> viene creato un elenco di tale tipo.

 Per ulteriori informazioni sul componente <xref:System.Windows.Forms.BindingSource>, vedere:

- [Componente BindingSource](https://msdn.microsoft.com/library/3e2faf4c-f5b8-4fa6-9fbc-f59c37ec2fb9)

- [Cenni preliminari sul componente BindingSource](https://msdn.microsoft.com/library/be838caf-fcb0-4b68-827f-58b2c04b747f)

- [Architettura del componente BindingSource](https://msdn.microsoft.com/library/7bc69c90-8a11-48b1-9336-3adab5b41591)

## <a name="bindingnavigator-control"></a>BindingNavigator (controllo)
 Questo componente fornisce un'interfaccia utente per spostarsi tra i dati visualizzati da un'applicazione Windows. Per altre informazioni, vedere [Controllo BindingNavigator](https://msdn.microsoft.com/library/18c1e2a5-9834-40d3-9b2e-2b545e4e769e).

## <a name="datagridview-control"></a>DataGridView (controllo)
 Per visualizzare e modificare dati tabulari da molti tipi diversi di origini dati, utilizzare il controllo <xref:System.Windows.Forms.DataGridView>. È possibile associare i dati a un <xref:System.Windows.Forms.DataGridView> usando la proprietà <xref:System.Windows.Forms.DataGridView.DataSource%2A>. Per altre informazioni, vedere [Cenni preliminari sul controllo DataGridView](https://msdn.microsoft.com/library/0a45c661-89dc-4390-9cc6-c47eee501488).

## <a name="see-also"></a>Vedere anche
 [Associare controlli ai dati in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)

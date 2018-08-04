---
title: Panoramica del modello di automazione | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio SDK], about automation
- extensibility
ms.assetid: 12b6d6db-0d22-4aaa-aa7d-1365f759b7b0
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: f8d6f5844f47e867d7c0442c9bb86e3722b40b27
ms.sourcegitcommit: 1c2ed640512ba613b3bbbc9ce348e28be6ca3e45
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/03/2018
ms.locfileid: "39498013"
---
# <a name="automation-model-overview"></a>Cenni preliminari sul modello di automazione
Il modello di automazione è costituito da un set di oggetti su cui è possibile scrivere un componente aggiuntivo di Visual Studio o estensione. Un componente aggiuntivo è un'applicazione che è possibile modificare l'ambiente di Visual Studio e automatizzare le attività comuni. Un'estensione di Visual Studio possa creare componenti personalizzati di Visual Studio o aggiungere la funzionalità dei componenti standard, ad esempio l'editor di testo.  
  
## <a name="objects-in-the-automation-model"></a>Oggetti nel modello di automazione  
 Il modello di automazione è costituito da gruppi di oggetti che consentono di controllare aspetti principali dell'ambiente comune correlati. Il diagramma seguente mostra il vasto set di oggetti di Visual Studio che costituiscono il modello di automazione.  
  
 ![Grafico di oggetti di Visual Studio automation](../../extensibility/internals/media/vsvisualstudioautomationobjectchart.gif "vsVisualStudioAutomationObjectChart")  
  
 Per altre informazioni, vedere [estendono l'ambiente di Visual Studio](http://msdn.microsoft.com/Library/4173a963-7ac7-4966-9bb7-e28a9d9f6792).  
  
 L'ambiente fornisce un modello per aree funzionali diverse. Ad esempio, vi è un modello di codice per diversi elementi che potrebbero risultare nel codice. È disponibile un modello di documento per vari elementi del documento. Un'area, l'area di progetto, è di particolare interesse per i provider di VSPackage. I nuovi tipi di progetto per contribuire al modello di automazione in modo analogo a come probabilmente si desidererà [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] e [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] contribuiscono al modello di automazione. Che procedura [fornire l'automazione per i pacchetti VSPackage](../../extensibility/internals/providing-automation-for-vspackages.md).  
  
 Posizioni in cui è possibile considerare l'estensione del modello di automazione dell'ambiente:  
  
-   Progetto  
  
-   Document  
  
-   Codice  
  
-   Compilazione  

  
Per altre informazioni sull'automazione, vedere [automazione ed estendibilità in Visual Studio](http://msdn.microsoft.com/Library/f71a2253-3e68-4e5e-9a18-edbba816caf6). Questo documento e i documenti vengono forniti collegamenti per poter prendere decisioni relative a come si deve fornire l'automazione per il pacchetto VSPackage.  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura: creare un componente aggiuntivo](http://msdn.microsoft.com/Library/50be56d2-e3a5-4cd2-8569-2a0666b268ce)
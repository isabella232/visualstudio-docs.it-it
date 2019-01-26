---
title: Panoramica del modello di automazione | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio SDK], about automation
- extensibility
ms.assetid: 12b6d6db-0d22-4aaa-aa7d-1365f759b7b0
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 65698c140647831ab329069e61e2cc5ea826d6e5
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "54992113"
---
# <a name="automation-model-overview"></a>Cenni preliminari sul modello di automazione
Il modello di automazione è costituito da un set di oggetti su cui è possibile scrivere un componente aggiuntivo di Visual Studio o estensione. Un componente aggiuntivo è un'applicazione che è possibile modificare l'ambiente di Visual Studio e automatizzare le attività comuni. Un'estensione di Visual Studio possa creare componenti personalizzati di Visual Studio o aggiungere la funzionalità dei componenti standard, ad esempio l'editor di testo.  
  
## <a name="objects-in-the-automation-model"></a>Oggetti nel modello di automazione  
 Il modello di automazione è costituito da gruppi di oggetti che consentono di controllare aspetti principali dell'ambiente comune correlati. Il diagramma seguente mostra il vasto set di oggetti di Visual Studio che costituiscono il modello di automazione.  
  
 ![Grafico di oggetti di Visual Studio automation](../../extensibility/internals/media/vsvisualstudioautomationobjectchart.gif "vsVisualStudioAutomationObjectChart")  
  
 Per altre informazioni, vedere [estendono l'ambiente di Visual Studio](https://msdn.microsoft.com/Library/4173a963-7ac7-4966-9bb7-e28a9d9f6792).  
  
 L'ambiente fornisce un modello per aree funzionali diverse. Ad esempio, vi è un modello di codice per diversi elementi che potrebbero risultare nel codice. È disponibile un modello di documento per vari elementi del documento. Un'area, l'area di progetto, è di particolare interesse per i provider di VSPackage. I nuovi tipi di progetto per contribuire al modello di automazione in modo analogo a come probabilmente si desidererà [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] e [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] contribuiscono al modello di automazione. Che procedura [fornire l'automazione per i pacchetti VSPackage](../../extensibility/internals/providing-automation-for-vspackages.md).  
  
 Posizioni in cui è possibile considerare l'estensione del modello di automazione dell'ambiente:  
  
-   Progetto  
  
-   Document  
  
-   Codice  
  
-   Compilazione  

  
Per altre informazioni sull'automazione, vedere [automazione ed estendibilità in Visual Studio](../extensibility-in-visual-studio.md). Questo documento e i documenti vengono forniti collegamenti per poter prendere decisioni relative a come si deve fornire l'automazione per il pacchetto VSPackage.  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura: Creare un componente aggiuntivo](https://msdn.microsoft.com/Library/50be56d2-e3a5-4cd2-8569-2a0666b268ce)
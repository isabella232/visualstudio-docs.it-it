---
title: Panoramica del modello di automazione | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio SDK], about automation
- extensibility
ms.assetid: 12b6d6db-0d22-4aaa-aa7d-1365f759b7b0
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e17164976062ec916074c6210be6ae42e8ea1d03
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "65699499"
---
# <a name="automation-model-overview"></a>Panoramica del modello di automazione
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Il modello di automazione è costituito da un set di oggetti in cui è possibile scrivere un componente aggiuntivo o un'estensione di Visual Studio. Un componente aggiuntivo è un'applicazione in grado di modificare l'ambiente di Visual Studio e di automatizzare le attività comuni. Un'estensione di Visual Studio può creare componenti personalizzati di Visual Studio o aggiungere alla funzionalità dei componenti standard, ad esempio l'editor di testo.  
  
## <a name="objects-in-the-automation-model"></a>Oggetti nel modello di automazione  
 Il modello di automazione è costituito da gruppi di oggetti correlati che controllano i facet principali dell'ambiente comune. Di seguito è riportato un diagramma che illustra l'ampio set di oggetti che compongono il modello di automazione.  
  
 ![Grafico del modello di automazione di Visual Studio](../../extensibility/internals/media/vsvisualstudioautomationobjectchart.gif "vsVisualStudioAutomationObjectChart")  
Oggetti di automazione di Visual Studio  
  
 Per altre informazioni, vedere [estensione dell'ambiente di Visual Studio](https://msdn.microsoft.com/library/4173a963-7ac7-4966-9bb7-e28a9d9f6792).  
  
 L'ambiente fornisce un modello per aree funzionali diverse. È ad esempio disponibile un modello di codice per vari elementi che potrebbero essere presenti nel codice. È disponibile un modello di documento per vari elementi del documento. Un'area, l'area del progetto, è di particolare interesse per i provider VSPackage. È probabile che si desideri che i nuovi tipi di progetto contribuiscano al modello di automazione in modo analogo a [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] e [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] contribuiscano al modello di automazione. Questo processo è descritto in fornire l' [automazione per i pacchetti VSPackage](../../extensibility/internals/providing-automation-for-vspackages.md).  
  
 Luoghi in cui è possibile estendere il modello di automazione dell'ambiente:  
  
- Progetto  
  
- Document  
  
- Codice  
  
- Compilare  
  
  Per altre informazioni sull'automazione, vedere [automazione ed estendibilità per Visual Studio](https://msdn.microsoft.com/library/f71a2253-3e68-4e5e-9a18-edbba816caf6). Questo documento e i documenti a cui forniscono i collegamenti consentono di prendere decisioni in merito a come fornire l'automazione per il pacchetto VSPackage.  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura: creare un componente aggiuntivo](https://msdn.microsoft.com/library/50be56d2-e3a5-4cd2-8569-2a0666b268ce)

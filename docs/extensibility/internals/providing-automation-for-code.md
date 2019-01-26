---
title: Automazione per il codice | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- CodeModel object
ms.assetid: 21cb3e63-f25c-404b-bc1d-a32ad0fdd4d5
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4adbc5385923e071e158734500e30a6a05832a1f
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "54976219"
---
# <a name="providing-automation-for-code"></a>Automazione per il codice
Creazione di un modello di automazione per il codice non è obbligatorio. il SDK di ambiente non è incluso un esempio per questa operazione. Per informazioni su modelli di codice, vedere il <xref:EnvDTE.CodeModel> oggetto.  
  
 Per implementare un modello di codice, è necessario implementare le interfacce che sono determinate dalla struttura dei dati interna. Gli oggetti devono essere derivati dal `IDispatch` classe.  
  
 Gli oggetti che si estendono, <xref:EnvDTE.CodeModel> e <xref:EnvDTE.FileCodeModel>, sono disponibili le <xref:EnvDTE.Project> dell'oggetto e simile al seguente:  
  
 <xref:EnvDTE.Project.CodeModel%2A>  
  
 <xref:EnvDTE.ProjectItem.FileCodeModel%2A>  
  
 È possibile scegliere di implementare solo il `CodeModel` o il `FileCodeModel` interfaccia nell'oggetto di cui si esce dalle `Project` e <xref:EnvDTE.ProjectItem> oggetti. Fornire qualsiasi funzionalità da questa interfaccia appropriata per il sistema di progetto.  
  
 Se si desidera aggiungere le funzionalità, ad esempio metodi o proprietà, che non sono disponibili dallo standard `CodeModel` e `FileCodeModel` interfacce, creare un'interfaccia che eredita da standard. Assicurarsi di documentare con il sistema di progetto in modo che gli utenti finali sarà in grado di cercare l'elemento. Restituire l'interfaccia standard, ma l'utente può chiamare il `QueryInterface` metodo o il cast all'interfaccia se è noto a esistere.  
  
## <a name="see-also"></a>Vedere anche  
 [Panoramica del modello di automazione](../../extensibility/internals/automation-model-overview.md)
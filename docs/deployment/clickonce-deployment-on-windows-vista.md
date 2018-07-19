---
title: Distribuzione ClickOnce in Windows Vista | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- UAC manifest generation
- ClickOnce deployment, Windows
- manifest generation
- Windows, ClickOnce deployment
ms.assetid: b21a0ebc-0ff6-4f49-8993-7d1ad3f8cac2
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e4113c2e33e3be97a5102f5e5eca0344087a49c6
ms.sourcegitcommit: 8ee7efb70a1bfebcb6dd9855b926a4ff043ecf35
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/17/2018
ms.locfileid: "39078397"
---
# <a name="clickonce-deployment-on-windows-vista"></a>Distribuzione ClickOnce in Windows Vista

Compilazione di applicazioni in Visual Studio per controllo Account utente (UAC) in Windows Vista in genere genera un manifesto incorporato, come dati binari con codifica XML nel file eseguibile dell'applicazione.  Le applicazioni ClickOnce and Registration-Free COM richiedono un manifesto esterno, in modo che Visual Studio genera un file per i progetti che contiene i dati di controllo dell'account utente invece di un manifesto incorporato. Per le distribuzioni di ClickOnce and Registration-Free COM, Visual Studio Usa le informazioni da un file denominato *manifest* per generare informazioni sul manifesto UAC esterno. Tutti gli altri casi, Visual Studio incorpora i dati di controllo dell'account utente nel file eseguibile dell'applicazione. 

Visual Studio offre le seguenti opzioni per la generazione del manifesto:  
  
-   Usare un manifesto incorporato. Incorporare i dati di controllo dell'account utente nel file eseguibile dell'applicazione ed eseguire come utente normale.  
  
     Questo è l'impostazione predefinita (a meno che non si usa ClickOnce). Questa impostazione supporta il consueto modo in cui viene eseguito Visual Studio in Windows Vista, con la generazione di un interni ed esterni un manifesto usando `AsInvoker`.  
  
-   Usare un manifesto esterno. Generare un manifesto esterno usando *manifest*.  
  
     Questo genera solo il manifesto esterno usando le informazioni contenute in *manifest*. Quando si pubblica un'applicazione tramite ClickOnce o COM senza registrazione, Visual Studio aggiunge *manifest* al progetto e quindi aggiunge questa opzione.  
  
-   Non utilizzare alcun manifesto. Creare l'applicazione senza un manifesto.  
  
     Questo approccio è noto anche come *virtualizzazione*. Usare questa opzione per la compatibilità con le applicazioni esistenti da versioni precedenti di Visual Studio.  
  
 Le nuove proprietà sono disponibili nel **applicazione** pagina di creazione progetti (Visual c# solo per i progetti) e nel formato di file di progetto MSBuild.  
  
 Il metodo per la configurazione di generazione del manifesto UAC nell'IDE di Visual Studio è diversa a seconda del tipo di progetto (Visual c# o Visual Basic).  
  
   * Per informazioni sulla configurazione di progetti Visual c# per la generazione di manifesti, vedere [Application Page, Project Designer (c#)](../ide/reference/application-page-project-designer-csharp.md).  
  
   * Per informazioni sulla configurazione di progetti Visual Basic per la generazione di manifesti, vedere [pagina dell'applicazione, creazione progetti (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Distribuzione e protezione ClickOnce](../deployment/clickonce-security-and-deployment.md)   
 [Autorizzazioni utente e Visual Studio](http://msdn.microsoft.com/en-us/d5c55084-1e7b-4b61-b478-137db01c0fc0)   
 [Application Page, Project Designer (C#)](../ide/reference/application-page-project-designer-csharp.md)  (Applicazione (pagina), Creazione progetti (C#))  
 [Pagina Applicazione, Creazione progetti (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md)
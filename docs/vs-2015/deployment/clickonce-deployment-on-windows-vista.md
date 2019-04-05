---
title: Distribuzione ClickOnce in Windows Vista | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
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
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 15af68e52a902003cd483cb6705ab4ded947f1a2
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58967421"
---
# <a name="clickonce-deployment-on-windows-vista"></a>Distribuzione ClickOnce in Windows Vista
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Compilazione di applicazioni in Visual Studio per controllo Account utente (UAC) in Windows Vista in genere genera un manifesto incorporato, come dati binari con codifica XML nel file eseguibile dell'applicazione. Poiché le applicazioni ClickOnce and Registration-Free COM è necessario un manifesto esterno, Visual Studio genera un file per questi tipi di progetto che contiene i dati di controllo dell'account utente invece di un manifesto incorporato. Per impostazione predefinita, Visual Studio Usa le informazioni da un file denominato manifest per generare informazioni di manifesto UAC esterne (per la distribuzione ClickOnce and Registration-Free COM) o da incorporare nel file eseguibile dell'applicazione (per tutti gli altri casi). Visual Studio offre le seguenti opzioni per la generazione del manifesto:  
  
- Usare un manifesto incorporato. Incorporare i dati di controllo dell'account utente nel file eseguibile dell'applicazione e vengono eseguite come utente normale.  
  
   Questo è l'impostazione predefinita (a meno che non si usa ClickOnce). Questa impostazione supporta la consuete modalità in cui viene eseguito Visual Studio in Windows Vista; vale a dire, la generazione di un manifesto interno ed esterno, entrambi con `AsInvoker`.  
  
- Usare un manifesto esterno. Generare un manifesto esterno usando l'app. manifest.  
  
   Questo genera solo il manifesto esterno usando le informazioni nell'app. manifest. Quando si pubblica un'applicazione tramite ClickOnce o COM senza registrazione, Visual Studio manifest vengono aggiunti al progetto e aggiunge questa opzione.  
  
- Non utilizzare alcun manifesto. Creare l'applicazione senza un manifesto.  
  
   Questo approccio è noto anche come *virtualizzazione*. Usare questa opzione per la compatibilità con le applicazioni esistenti da versioni precedenti di Visual Studio.  
  
  Le nuove proprietà sono disponibili nel **applicazione** pagina di creazione progetti (Visual c# solo per i progetti) e nel formato di file di progetto MSBuild.  
  
  Si noti che il metodo per la configurazione di generazione del manifesto UAC nell'IDE di Visual Studio è diversa a seconda del tipo di progetto (Visual c# e Visual Basic).  
  
  Per informazioni sulla configurazione di progetti Visual c# per la generazione di manifesti, vedere [Application Page, Project Designer (c#)](../ide/reference/application-page-project-designer-csharp.md).  
  
  Per informazioni sulla configurazione di progetti Visual Basic per la generazione di manifesti, vedere [pagina dell'applicazione, creazione progetti (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Sicurezza e distribuzione di ClickOnce](../deployment/clickonce-security-and-deployment.md)   
 [Le autorizzazioni utente e Visual Studio](http://msdn.microsoft.com/d5c55084-1e7b-4b61-b478-137db01c0fc0)   
 [Application Page, Project Designer (C#)](../ide/reference/application-page-project-designer-csharp.md)  (Applicazione (pagina), Creazione progetti (C#))  
 [Pagina Applicazione, Creazione progetti (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md)

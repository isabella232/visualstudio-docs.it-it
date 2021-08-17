---
title: ClickOnce Distribuzione in Windows Vista | Microsoft Docs
description: Informazioni su come Visual Studio manifesto di Controllo dell'account utente esterno per ClickOnce e Registration-Free applicazioni COM, che richiedono un manifesto esterno.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
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
manager: jmartens
ms.technology: vs-ide-deployment
ms.workload:
- multiple
ms.openlocfilehash: f4b19059170e0c296cc7544bc62545691756b8a3
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122104972"
---
# <a name="clickonce-deployment-on-windows-vista"></a>Distribuzione ClickOnce in Windows Vista

La compilazione di applicazioni in Visual Studio per il controllo dell'account utente in Windows Vista genera in genere un manifesto incorporato, codificato come dati XML binari nel file eseguibile dell'applicazione.  ClickOnce e Registration-Free applicazioni COM richiedono un manifesto esterno, quindi Visual Studio genera un file per questi progetti che contiene i dati di Controllo dell'account utente anziché un manifesto incorporato. Per ClickOnce e Registration-Free com, Visual Studio usa le informazioni di un file denominato *app.manifest* per generare informazioni sul manifesto del controllo dell'account utente esterno. Per tutti gli altri casi, Visual Studio incorpora i dati di Controllo dell'account utente nel file eseguibile dell'applicazione.

Visual Studio offre le opzioni seguenti per la generazione del manifesto:

- Usare un manifesto incorporato. Incorporare i dati di Controllo dell'account utente nel file eseguibile dell'applicazione ed eseguirsi come utente normale.

   Questa è l'impostazione predefinita , a meno che non si usi ClickOnce. Questa impostazione supporta il modo consueto in cui Visual Studio opera su Windows Vista, con la generazione di un manifesto interno ed esterno usando `AsInvoker` .

- Usare un manifesto esterno. Generare un manifesto esterno usando *app.manifest.*

   Viene generato solo il manifesto esterno usando le informazioni in *app.manifest.* Quando si pubblica un'applicazione usando ClickOnce o Registration-Free COM, Visual Studio *aggiunge app.manifest* al progetto e quindi aggiunge questa opzione.

- Non usare alcun manifesto. Creare l'applicazione senza un manifesto.

   Questo approccio è noto anche come *virtualizzazione.* Usare questa opzione per la compatibilità con le applicazioni esistenti di versioni precedenti di Visual Studio.

  Le nuove proprietà sono  disponibili nella pagina Applicazione di Progettazione Project (solo per i progetti Visual C#) e nel formato MSBuild file di progetto.

  Il metodo per la configurazione della generazione del manifesto di Controllo dell'account utente nell'IDE di Visual Studio varia a seconda del tipo di progetto (Visual C# o Visual Basic).

  * Per informazioni sulla configurazione di progetti Visual C# per la generazione di manifesti, vedere [Pagina Applicazione, progettazione Project (C#).](../ide/reference/application-page-project-designer-csharp.md)

  * Per informazioni sulla configurazione di Visual Basic per la generazione di manifesti, vedere Pagina Applicazione, progettazione Project [(Visual Basic).](../ide/reference/application-page-project-designer-visual-basic.md)

## <a name="see-also"></a>Vedi anche
- [Sicurezza e distribuzione di ClickOnce](../deployment/clickonce-security-and-deployment.md)
- [Autorizzazioni utente e Visual Studio](/previous-versions/ms165100(v=vs.100))
- [Applicazione (pagina), Creazione progetti (C#)](../ide/reference/application-page-project-designer-csharp.md)
- [Application Page, Project Designer (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md)
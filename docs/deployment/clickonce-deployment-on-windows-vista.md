---
title: Distribuzione ClickOnce in Windows Vista | Microsoft Docs
description: Informazioni su come Visual Studio genera un manifesto External UAC per ClickOnce e Registration-Free applicazioni COM, che richiedono un manifesto esterno.
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c2e09225339a87c55c31d27d26b129e199385e99
ms.sourcegitcommit: 0893244403aae9187c9375ecf0e5c221c32c225b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/09/2020
ms.locfileid: "94383079"
---
# <a name="clickonce-deployment-on-windows-vista"></a>Distribuzione ClickOnce in Windows Vista

La compilazione di applicazioni in Visual Studio per il controllo dell'account utente in Windows Vista genera in genere un manifesto incorporato, codificato come dati XML binari nel file eseguibile dell'applicazione.  Le applicazioni ClickOnce e Registration-Free COM richiedono un manifesto esterno, quindi Visual Studio genera un file per questi progetti contenenti i dati UAC anziché un manifesto incorporato. Per le distribuzioni ClickOnce e Registration-Free COM, Visual Studio usa le informazioni di un file denominato *app. manifest* per generare informazioni sul manifesto del controllo dell'account utente esterno. Per tutti gli altri casi, in Visual Studio i dati del controllo dell'account utente vengono incorporati nel file eseguibile dell'applicazione.

Visual Studio offre le opzioni seguenti per la generazione di manifesti:

- Utilizzare un manifesto incorporato. Incorporare i dati UAC nel file eseguibile dell'applicazione ed eseguirli come utente normale.

   Si tratta dell'impostazione predefinita, a meno che non si usi ClickOnce. Questa impostazione supporta il solito modo in cui Visual Studio opera su Windows Vista, con la generazione di un manifesto interno ed esterno tramite `AsInvoker` .

- Utilizzare un manifesto esterno. Generare un manifesto esterno usando *app. manifest*.

   Viene generato solo il manifesto esterno usando le informazioni in *app. manifest*. Quando si pubblica un'applicazione tramite ClickOnce o Registration-Free COM, Visual Studio aggiunge *app. manifest* al progetto e quindi aggiunge questa opzione.

- Non usare alcun manifesto. Creare l'applicazione senza un manifesto.

   Questo approccio è noto anche come *virtualizzazione*. Usare questa opzione per la compatibilità con le applicazioni esistenti da versioni precedenti di Visual Studio.

  Le nuove proprietà sono disponibili nella pagina **applicazione** di progettazione progetti (solo per i progetti Visual C#) e nel formato di file di progetto MSBuild.

  Il metodo per configurare la generazione del manifesto UAC nell'IDE di Visual Studio varia a seconda del tipo di progetto (Visual C# o Visual Basic).

  * Per informazioni sulla configurazione di progetti Visual C# per la generazione di manifesti, vedere [pagina applicazione, Progettazione progetti (C#)](../ide/reference/application-page-project-designer-csharp.md).

  * Per informazioni sulla configurazione di progetti Visual Basic per la generazione di manifesti, vedere [pagina applicazione, Progettazione progetti (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md).

## <a name="see-also"></a>Vedere anche
- [Sicurezza e distribuzione di ClickOnce](../deployment/clickonce-security-and-deployment.md)
- [Autorizzazioni utente e Visual Studio](/previous-versions/ms165100(v=vs.100))
- [Applicazione (pagina), Creazione progetti (C#)](../ide/reference/application-page-project-designer-csharp.md)
- [Application Page, Project Designer (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md)
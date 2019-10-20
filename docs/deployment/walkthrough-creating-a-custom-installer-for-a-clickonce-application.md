---
title: Creare un programma di installazione personalizzato per l'applicazione ClickOnce
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, custom installer
- installer [ClickOnce], custom
- deploying applications [ClickOnce], custom installer
- InPlaceHostingManager [ClickOnce], custom installer
- custom installer [ClickOnce]
ms.assetid: fb222cc5-8aeb-4b94-8c49-b93e342f5f69
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b648134b7ad27a8f622ce270dc0f05e0a7e6516c
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72637414"
---
# <a name="walkthrough-create-a-custom-installer-for-a-clickonce-application"></a>Procedura dettagliata: creare un programma di installazione personalizzato per un'applicazione ClickOnce
Qualsiasi applicazione ClickOnce basata su un file con *estensione exe* può essere installata e aggiornata automaticamente da un programma di installazione personalizzato. Un programma di installazione personalizzato può implementare un'esperienza utente personalizzata durante l'installazione, incluse le finestre di dialogo personalizzate per la sicurezza e le operazioni di manutenzione. Per eseguire le operazioni di installazione, il programma di installazione personalizzato usa la classe <xref:System.Deployment.Application.InPlaceHostingManager>. In questa procedura dettagliata viene illustrato come creare un programma di installazione personalizzato che installa automaticamente un'applicazione ClickOnce.

## <a name="prerequisites"></a>Prerequisites

### <a name="to-create-a-custom-clickonce-application-installer"></a>Per creare un programma di installazione di un'applicazione ClickOnce personalizzata

1. Nell'applicazione ClickOnce aggiungere riferimenti a System. Deployment e System. Windows. Forms.

2. Aggiungere una nuova classe all'applicazione e specificare un nome. Questa procedura dettagliata usa il nome `MyInstaller`.

3. Aggiungere le direttive `Imports` o `using` seguenti all'inizio della nuova classe.

    ```vb
    Imports System.Deployment.Application
    Imports System.Windows.Forms
    ```

    ```csharp
    using System.Deployment.Application;
    using System.Windows.Forms;
    ```

4. Aggiungere i metodi seguenti alla classe.

     Questi metodi chiamano <xref:System.Deployment.Application.InPlaceHostingManager> metodi per scaricare il manifesto di distribuzione, dichiarare le autorizzazioni appropriate, richiedere all'utente l'autorizzazione per installare, quindi scaricare e installare l'applicazione nella cache ClickOnce. Un programma di installazione personalizzato può specificare che un'applicazione ClickOnce è già attendibile oppure può rinviare la decisione di attendibilità alla chiamata al metodo <xref:System.Deployment.Application.InPlaceHostingManager.AssertApplicationRequirements%2A>. Questo codice precede l'attendibilità dell'applicazione.

    > [!NOTE]
    > Le autorizzazioni assegnate da pre-trusting non possono superare le autorizzazioni del codice del programma di installazione personalizzato.

     [!code-vb[System.Deployment.Application.InPlaceHostingManager#1](../deployment/codesnippet/VisualBasic/walkthrough-creating-a-custom-installer-for-a-clickonce-application_1.vb)]
     [!code-csharp[System.Deployment.Application.InPlaceHostingManager#1](../deployment/codesnippet/CSharp/walkthrough-creating-a-custom-installer-for-a-clickonce-application_1.cs)]

5. Per tentare l'installazione dal codice, chiamare il metodo `InstallApplication`. Se, ad esempio, è stato denominato `MyInstaller` della classe, è possibile chiamare `InstallApplication` nel modo seguente.

    ```vb
    Dim installer As New MyInstaller()
    installer.InstallApplication("\\myServer\myShare\myApp.application")
    MessageBox.Show("Installer object created.")
    ```

    ```csharp
    MyInstaller installer = new MyInstaller();
    installer.InstallApplication(@"\\myServer\myShare\myApp.application");
    MessageBox.Show("Installer object created.");
    ```

## <a name="next-steps"></a>Passaggi successivi
 Un'applicazione ClickOnce può anche aggiungere la logica di aggiornamento personalizzata, inclusa un'interfaccia utente personalizzata da visualizzare durante il processo di aggiornamento. Per ulteriori informazioni, vedere <xref:System.Deployment.Application.UpdateCheckInfo>. Un'applicazione ClickOnce può inoltre eliminare la voce del menu Start standard, il collegamento e l'aggiunta o la rimozione di programmi utilizzando un elemento `<customUX>`. Per ulteriori informazioni, vedere [\<entryPoint elemento >](../deployment/entrypoint-element-clickonce-application.md) e <xref:System.Deployment.Application.DownloadApplicationCompletedEventArgs.ShortcutAppId%2A>.

## <a name="see-also"></a>Vedere anche
- [Manifesto dell'applicazione ClickOnce](../deployment/clickonce-application-manifest.md)
- [elemento \<entryPoint >](../deployment/entrypoint-element-clickonce-application.md)

---
title: "Procedura dettagliata: Creazione di un programma di installazione personalizzato per un'applicazione ClickOnce | Microsoft Docs"
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
ms.openlocfilehash: 7ceadc2458b6d380cc67062cf89cbea20541446c
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 02/21/2019
ms.locfileid: "56609944"
---
# <a name="walkthrough-create-a-custom-installer-for-a-clickonce-application"></a>Procedura dettagliata: Creare un programma di installazione personalizzato per un'applicazione ClickOnce
Tutte le applicazioni ClickOnce basato su un *.exe* file può essere installati e aggiornati da un programma di installazione personalizzato in modo invisibile. Un programma di installazione personalizzato può implementare un'esperienza utente migliorata durante l'installazione, tra cui finestre di dialogo personalizzate per le operazioni di manutenzione e sicurezza. Per eseguire operazioni di installazione, il programma di installazione personalizzato utilizza il <xref:System.Deployment.Application.InPlaceHostingManager> classe. Questa procedura dettagliata viene illustrato come creare un programma di installazione personalizzato per l'installazione invisibile all'utente un'applicazione ClickOnce.

## <a name="prerequisites"></a>Prerequisiti

### <a name="to-create-a-custom-clickonce-application-installer"></a>Per creare un programma di installazione di applicazioni ClickOnce personalizzato

1.  Nell'applicazione ClickOnce, aggiungere i riferimenti a System. Deployment e Forms.

2.  Aggiungere una nuova classe all'applicazione e specificare un nome qualsiasi. Questa procedura dettagliata usa il nome `MyInstaller`.

3.  Aggiungere il codice seguente `Imports` o `using` istruzioni all'inizio della nuova classe.

    ```vb
    Imports System.Deployment.Application
    Imports System.Windows.Forms
    ```

    ```csharp
    using System.Deployment.Application;
    using System.Windows.Forms;
    ```

4.  Aggiungere i metodi seguenti alla classe.

     Questi metodi chiamano <xref:System.Deployment.Application.InPlaceHostingManager> metodi per scaricare il manifesto di distribuzione, l'asserzione delle autorizzazioni appropriate, chiedere all'utente l'autorizzazione per installare e quindi scaricare e installare l'applicazione nella cache di ClickOnce. Un programma di installazione personalizzato è possibile specificare che un'applicazione ClickOnce è pre-attendibile o possibile posticipare la decisione di attendibilità di <xref:System.Deployment.Application.InPlaceHostingManager.AssertApplicationRequirements%2A> chiamata al metodo. Questo codice pre-attendibile l'applicazione.

    > [!NOTE]
    >  Le autorizzazioni assegnate da pre-concessione dell'attendibilità non possono superare le autorizzazioni del codice di programma di installazione personalizzato.

     [!code-vb[System.Deployment.Application.InPlaceHostingManager#1](../deployment/codesnippet/VisualBasic/walkthrough-creating-a-custom-installer-for-a-clickonce-application_1.vb)]
     [!code-csharp[System.Deployment.Application.InPlaceHostingManager#1](../deployment/codesnippet/CSharp/walkthrough-creating-a-custom-installer-for-a-clickonce-application_1.cs)]

5.  Per tentare l'installazione dal codice, chiamare il `InstallApplication` (metodo). Ad esempio, se la classe è denominata `MyInstaller`, è possibile chiamare `InstallApplication` nel modo seguente.

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
 Un'applicazione ClickOnce è anche possibile aggiungere logica di aggiornamento personalizzato, inclusi un'interfaccia utente personalizzata per mostrare durante il processo di aggiornamento. Per ulteriori informazioni, vedere <xref:System.Deployment.Application.UpdateCheckInfo>. Un'applicazione ClickOnce può anche eliminare la voce di menu Start standard, collegamento e Aggiungi / Rimuovi programmi voce usando un `<customUX>` elemento. Per altre informazioni, vedere [ \<entryPoint > elemento](../deployment/entrypoint-element-clickonce-application.md) e <xref:System.Deployment.Application.DownloadApplicationCompletedEventArgs.ShortcutAppId%2A>.

## <a name="see-also"></a>Vedere anche
- [Manifesto dell'applicazione ClickOnce](../deployment/clickonce-application-manifest.md)
- [\<entryPoint > elemento](../deployment/entrypoint-element-clickonce-application.md)
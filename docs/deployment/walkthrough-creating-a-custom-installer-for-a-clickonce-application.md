---
title: Creare un programma di installazione personalizzato per ClickOnce appalta
description: Informazioni su come un programma di installazione personalizzato può installare e aggiornare automaticamente un'ClickOnce in base a un file .exe.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: vs-ide-deployment
ms.workload:
- multiple
ms.openlocfilehash: 4d19a93710b2134f7c4878faf8143209bff4e357
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126709873"
---
# <a name="walkthrough-create-a-custom-installer-for-a-clickonce-application"></a>Procedura dettagliata: Creare un programma di installazione personalizzato per un'ClickOnce personalizzata
Qualsiasi ClickOnce basata su un file *.exe* può essere installata e aggiornata automaticamente da un programma di installazione personalizzato. Un programma di installazione personalizzato può implementare un'esperienza utente personalizzata durante l'installazione, incluse le finestre di dialogo personalizzate per le operazioni di sicurezza e manutenzione. Per eseguire operazioni di installazione, il programma di installazione personalizzato usa la <xref:System.Deployment.Application.InPlaceHostingManager> classe . Questa procedura dettagliata illustra come creare un programma di installazione personalizzato che installa automaticamente un'ClickOnce personalizzata.

## <a name="prerequisites"></a>Prerequisiti

### <a name="to-create-a-custom-clickonce-application-installer"></a>Per creare un programma di installazione ClickOnce personalizzato

1. Nell'ClickOnce aggiungere riferimenti a System.Deployment e System. Windows. Forme.

2. Aggiungere una nuova classe all'applicazione e specificare qualsiasi nome. Questa procedura dettagliata usa il nome `MyInstaller`.

3. Aggiungere le `Imports` direttive o seguenti `using` all'inizio della nuova classe.

    ```vb
    Imports System.Deployment.Application
    Imports System.Windows.Forms
    ```

    ```csharp
    using System.Deployment.Application;
    using System.Windows.Forms;
    ```

4. Aggiungere i metodi seguenti alla classe .

     Questi metodi chiamano metodi per scaricare il manifesto della distribuzione, asserire le autorizzazioni appropriate, chiedere all'utente l'autorizzazione per l'installazione e quindi scaricare e installare <xref:System.Deployment.Application.InPlaceHostingManager> l'applicazione nella cache ClickOnce. Un programma di installazione personalizzato può specificare che ClickOnce'applicazione è pre-attendibile o può rinviare la decisione di attendibilità alla <xref:System.Deployment.Application.InPlaceHostingManager.AssertApplicationRequirements%2A> chiamata al metodo . Questo codice pre-considera attendibile l'applicazione.

    > [!NOTE]
    > Le autorizzazioni assegnate dalla pre-attendibilità non possono superare le autorizzazioni del codice del programma di installazione personalizzato.

    :::code language="vb" source="../snippets/visualbasic/VS_Snippets_Winforms/System.Deployment.Application.InPlaceHostingManager/VB/Form1.vb" id="Snippet1":::
    :::code language="csharp" source="../snippets/csharp/VS_Snippets_Winforms/System.Deployment.Application.InPlaceHostingManager/CS/Form1.cs" id="Snippet1":::

5. Per tentare l'installazione dal codice, chiamare il `InstallApplication` metodo . Ad esempio, se la classe è stata denominata `MyInstaller` , è possibile chiamare nel modo `InstallApplication` seguente.

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
 Un ClickOnce app applicazione può anche aggiungere logica di aggiornamento personalizzata, inclusa un'interfaccia utente personalizzata da visualizzare durante il processo di aggiornamento. Per altre informazioni, vedere <xref:System.Deployment.Application.UpdateCheckInfo>. Un'ClickOnce applicazione può anche eliminare la voce standard menu Start, il collegamento e la voce Installazione applicazioni usando un `<customUX>` elemento . Per altre informazioni, [ \<entryPoint> vedere](../deployment/entrypoint-element-clickonce-application.md) element e <xref:System.Deployment.Application.DownloadApplicationCompletedEventArgs.ShortcutAppId%2A> .

## <a name="see-also"></a>Vedi anche
- [ClickOnce dell'applicazione](../deployment/clickonce-application-manifest.md)
- [\<entryPoint> Elemento](../deployment/entrypoint-element-clickonce-application.md)

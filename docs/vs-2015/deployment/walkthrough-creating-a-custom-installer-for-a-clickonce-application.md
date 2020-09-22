---
title: "Procedura dettagliata: creazione di un programma di installazione personalizzato per un'applicazione ClickOnce | Microsoft Docs"
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
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
caps.latest.revision: 36
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 9ebde75fdf36c84f40ae660a24d469c36e72ceaf
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "90839983"
---
# <a name="walkthrough-creating-a-custom-installer-for-a-clickonce-application"></a>Procedura dettagliata: creazione di un programma di installazione personalizzato per un'applicazione ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Qualsiasi applicazione ClickOnce basata su un file con estensione exe può essere installata e aggiornata automaticamente da un programma di installazione personalizzato. Un programma di installazione personalizzato può implementare un'esperienza utente personalizzata durante l'installazione, incluse le finestre di dialogo personalizzate per la sicurezza e le operazioni di manutenzione. Per eseguire le operazioni di installazione, il programma di installazione personalizzato usa la <xref:System.Deployment.Application.InPlaceHostingManager> classe. In questa procedura dettagliata viene illustrato come creare un programma di installazione personalizzato che installa automaticamente un'applicazione ClickOnce.  
  
## <a name="prerequisites"></a>Prerequisiti  
  
### <a name="to-create-a-custom-clickonce-application-installer"></a>Per creare un programma di installazione di un'applicazione ClickOnce personalizzata  
  
1. Nell'applicazione ClickOnce aggiungere riferimenti a System. Deployment e System. Windows. Forms.  
  
2. Aggiungere una nuova classe all'applicazione e specificare un nome. Questa procedura dettagliata usa il nome `MyInstaller`.  
  
3. Aggiungere le `Imports` istruzioni o seguenti `using` all'inizio della nuova classe.  
  
    ```vb  
    Imports System.Deployment.Application  
    Imports System.Windows.Forms  
    ```  
  
    ```csharp  
    using System.Deployment.Application;  
    using System.Windows.Forms;  
    ```  
  
4. Aggiungere i metodi seguenti alla classe.  
  
     Questi metodi chiamano i <xref:System.Deployment.Application.InPlaceHostingManager> metodi per scaricare il manifesto di distribuzione, dichiarare le autorizzazioni appropriate, richiedere all'utente l'autorizzazione per l'installazione e quindi scaricare e installare l'applicazione nella cache ClickOnce. Un programma di installazione personalizzato può specificare che un'applicazione ClickOnce è già attendibile oppure può rinviare la decisione di attendibilità alla <xref:System.Deployment.Application.InPlaceHostingManager.AssertApplicationRequirements%2A> chiamata al metodo. Questo codice precede l'attendibilità dell'applicazione.  
  
    > [!NOTE]
    > Le autorizzazioni assegnate da pre-trusting non possono superare le autorizzazioni del codice del programma di installazione personalizzato.  
  
     [!code-csharp[System.Deployment.Application.InPlaceHostingManager#1](../snippets/csharp/VS_Snippets_Winforms/System.Deployment.Application.InPlaceHostingManager/CS/Form1.cs#1)]
     [!code-vb[System.Deployment.Application.InPlaceHostingManager#1](../snippets/visualbasic/VS_Snippets_Winforms/System.Deployment.Application.InPlaceHostingManager/VB/Form1.vb#1)]  
  
5. Per tentare l'installazione dal codice, chiamare il `InstallApplication` metodo. Se ad esempio è stata denominata la classe `MyInstaller` , è possibile chiamare `InstallApplication` nel modo seguente.  
  
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
 Un'applicazione ClickOnce può anche aggiungere la logica di aggiornamento personalizzata, inclusa un'interfaccia utente personalizzata da visualizzare durante il processo di aggiornamento. Per altre informazioni, vedere <xref:System.Deployment.Application.UpdateCheckInfo>. Un'applicazione ClickOnce può inoltre eliminare la voce del menu Start standard, il collegamento e l'aggiunta o la rimozione di programmi utilizzando un `<customUX>` elemento. Per ulteriori informazioni, vedere [ \<entryPoint> elemento](../deployment/entrypoint-element-clickonce-application.md) e <xref:System.Deployment.Application.DownloadApplicationCompletedEventArgs.ShortcutAppId%2A> .  
  
## <a name="see-also"></a>Vedere anche  
 [Manifesto dell'applicazione ClickOnce](../deployment/clickonce-application-manifest.md)   
 [\<entryPoint> Elemento](../deployment/entrypoint-element-clickonce-application.md)

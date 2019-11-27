---
title: Risoluzione dei problemi e problemi noti (Visual Studio Tools per Unity) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-unity-tools
ms.topic: troubleshooting
ms.assetid: 8f5db192-8d78-4627-bd07-dbbc803ac554
caps.latest.revision: 7
author: conceptdev
ms.author: crdun
manager: jillfra
ms.openlocfilehash: ad085cc6c41714a551fbb344274e6d0f164ab67e
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2019
ms.locfileid: "74297655"
---
# <a name="troubleshooting-and-known-issues-visual-studio-tools-for-unity"></a>Risoluzione dei problemi e problemi noti (Visual Studio Tools per Unity)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In questa sezione verranno illustrate le soluzioni a problemi comuni relativi a Visual Studio Tools per Unity. Oltre alla descrizione dei problemi noti, verrà spiegato come contribuire al miglioramento di Visual Studio Tools per Unity segnalando gli errori.  
  
## <a name="troubleshooting"></a>Risoluzione dei problemi  
 Per risolvere alcuni problemi comuni relativi a Visual Studio Tools per Unity, vedere le sezioni seguenti.  
  
### <a name="migrating-from-unityvs-to-visual-studio-tools-for-unity"></a>Migrazione da UnityVS a Visual Studio Tools per Unity  
 Se si intende eseguire la migrazione da UnityVS a Visual Studio Tools per Unity, è necessario generare nuove soluzioni Visual Studio per i progetti Unity.  
  
##### <a name="to-migrate-your-unity-project-from-unityvs-18-to-visual-studio-tools-for-unity-19"></a>Per eseguire la migrazione del progetto Unity da UnityVS 1.8 a Visual Studio Tools per Unity 1.9  
  
1. Eliminare i vecchi file della soluzione e del progetto dal progetto Unity. Nella directory radice del progetto Unity individuare i file con estensione sln di Visual Studio e i file * proj, quindi eliminarli tutti.  
  
2. Importare il pacchetto di Visual Studio Tools per Unity nel progetto Unity. Per informazioni su come importare il pacchetto VSTU, vedere Configurare Visual Studio Tools per Unity nella pagina [Introduzione](../cross-platform/getting-started-with-visual-studio-tools-for-unity.md) .  
  
3. Generare i nuovi file della soluzione e del progetto. Per generarli subito, nel menu principale dell'editor di Unity scegliere **Visual Studio Tools**, **Generate Project Files**. In caso contrario, è possibile ignorare questo passaggio. Visual Studio Tools per Unity genererà i nuovi file automaticamente quando si sceglie **Visual Studio Tools**, **Open in Visual Studio**.  
  
### <a name="visual-studio-wont-load-the-solution-that-visual-studio-tools-for-unity-created"></a>Visual Studio non carica la soluzione creata in Visual Studio Tools per Unity  
 Per altre informazioni, vedere la [risposta a questa domanda in stackoverflow](https://stackoverflow.com/questions/20086755/unityvs-visual-studio-can-not-open/24035907#24035907).  
  
### <a name="on-windows-8-visual-studio-asks-to-download-the-unity-target-framework"></a>In Windows 8 Visual Studio chiede di scaricare il framework di destinazione Unity  
 UnityVS richiede .NET Framework 3.5, che in Windows 8 non è installato per impostazione predefinita. Per risolvere questo problema, seguire le istruzioni per scaricare e installare .NET Framework 3.5.  
  
## <a name="known-issues"></a>Problemi noti  
 In Visual Studio Tools per Unity sono presenti problemi noti derivanti dall'interazione tra il debugger e la versione precedente del compilatore C# inclusa in Unity. Microsoft sta lavorando per risolvere questi problemi, ma nel frattempo potrebbero verificarsi i problemi seguenti.  
  
- Durante il debug si verifica talvolta un arresto anomalo di Unity.  
  
- Durante il debug si verifica talvolta un blocco di Unity.  
  
- Durante l'esecuzione o l'uscita da istruzioni o metodi vengono riscontrati comportamenti errati, in particolare negli iteratori o all'interno di istruzioni switch.  
  
## <a name="reporting-errors"></a>Segnalazione di errori  
 È possibile contribuire a migliorare la qualità di Visual Studio Tools per Unity inviando apposite segnalazioni quando si riscontrano arresti anomali, blocchi o errori di altro tipo. In questo modo Microsoft potrà esaminare e correggere i problemi relativi a Visual Studio Tools per Unity. Grazie.  
  
### <a name="how-to-report-an-error-when-visual-studio-freezes"></a>Come segnalare un errore in caso di blocco di Visual Studio  
 Sono stati segnalati alcuni casi di blocco di Visual Studio durante il debug con Visual Studio Tools per Unity, ma sono necessari maggiori dati per analizzare questo problema. Per contribuire alla risoluzione del problema, eseguire le operazioni descritte di seguito.  
  
##### <a name="to-report-that-visual-studio-freezes-while-debugging-with-visual-studio-tools-for-unity"></a>Per segnalare un blocco di Visual Studio durante il debug con Visual Studio Tools per Unity  
  
1. Aprire una nuova istanza di Visual Studio.  
  
2. Aprire la finestra di dialogo Connetti a processo. Nel menu principale della nuova istanza di Visual Studio scegliere **Debug**, **Connetti a processo**.  
  
3. Connettere il debugger all'istanza bloccata di Visual Studio. Nella finestra di dialogo **Connetti a processo** selezionare l'istanza bloccata di Visual Studio dalla tabella **Processi disponibili** e quindi fare clic sul pulsante **Connetti** .  
  
4. Sospendere l'esecuzione del debugger. Nel menu principale della nuova istanza di Visual Studio scegliere **Debug**, **Interrompi tutto** oppure premere **CTRL+ALT+INTERR**.  
  
5. Creare un dump del thread. Nella finestra Comando immettere il seguente comando e premere **INVIO**:  
  
   ```powershell  
   Debug.ListCallStack /AllThreads /ShowExternalCode  
   ```  
  
    Potrebbe essere necessario rendere prima visibile la finestra **Comando** . Nel menu principale di Visual Studio scegliere **Visualizza**, **Altre finestre**, **Finestra di comando**.  
  
6. Inviare infine il dump del thread all'indirizzo [vstusp@microsoft.com](mailto:vstusp@microsoft.com), insieme a una descrizione dell'operazione in corso quando si è verificato il blocco di Visual Studio.

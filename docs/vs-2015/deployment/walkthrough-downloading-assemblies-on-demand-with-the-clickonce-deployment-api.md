---
title: "Procedura dettagliata: download di assembly su richiesta con l'API di distribuzione ClickOnce | Microsoft Docs"
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- assemblies, downloading [ClickOnce]
- ClickOnce deployment, on-demand download
- on-demand assemblies, ClickOnce
ms.assetid: d20e2789-8621-4806-b5b7-841122da1456
caps.latest.revision: 18
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: af03329a05501427f6d04d6cddbd637c3311b339
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "90839691"
---
# <a name="walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api"></a>Procedura dettagliata: download di assembly su richiesta con l'API della distribuzione ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Per impostazione predefinita, tutti gli assembly inclusi in un' [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] applicazione vengono scaricati quando l'applicazione viene eseguita per la prima volta. Tuttavia, è possibile che si disponga di parti dell'applicazione utilizzate da un piccolo set di utenti. In questo caso, è consigliabile scaricare un assembly solo quando si crea uno dei relativi tipi. La procedura dettagliata riportata di seguito illustra come contrassegnare come "facoltativi" determinati assembly nell'applicazione e come scaricarli tramite le classi nello spazio dei nomi <xref:System.Deployment.Application> quando sono richiesti da Common Language Runtime (CLR).  
  
> [!NOTE]
> Per usare questa procedura, è necessario eseguire l'applicazione con attendibilità totale.  
  
## <a name="prerequisites"></a>Prerequisiti  
 Per completare questa procedura dettagliata, sarà necessario uno dei componenti seguenti:  
  
- Windows SDK. Il Windows SDK può essere scaricato dall'area download Microsoft.  
  
- Visual Studio.  
  
## <a name="creating-the-projects"></a>Creazione dei progetti  
  
#### <a name="to-create-a-project-that-uses-an-on-demand-assembly"></a>Per creare un progetto che usa un assembly su richiesta  
  
1. Creare una directory denominata ClickOnceOnDemand.  
  
2. Aprire il prompt dei comandi di Windows SDK o il [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] prompt dei comandi.  
  
3. Passare alla directory ClickOnceOnDemand  
  
4. Generare una coppia di chiavi pubblica/privata usando il comando seguente:  
  
    ```  
    sn -k TestKey.snk  
    ```  
  
5. Utilizzando blocco note o un altro editor di testo, definire una classe denominata `DynamicClass` con una singola proprietà denominata `Message` .  
  
     [!code-csharp[ClickOnceLibrary#1](../snippets/csharp/VS_Snippets_Winforms/ClickOnceLibrary/CS/Class1.cs#1)]
     [!code-vb[ClickOnceLibrary#1](../snippets/visualbasic/VS_Snippets_Winforms/ClickOnceLibrary/VB/Class1.vb#1)]  
  
6. Salvare il testo come file denominato `ClickOnceLibrary.cs` o `ClickOnceLibrary.vb` , a seconda del linguaggio usato, nella directory ClickOnceOnDemand  
  
7. Compilare il file in un assembly.  
  
    ```csharp  
    csc /target:library /keyfile:TestKey.snk ClickOnceLibrary.cs  
    ```  
  
    ```vb  
    vbc /target:library /keyfile:TestKey.snk ClickOnceLibrary.vb  
    ```  
  
8. Per ottenere il token di chiave pubblica per l'assembly, usare il comando seguente:  
  
    ```  
    sn -T ClickOnceLibrary.dll  
    ```  
  
9. Creare un nuovo file con l'editor di testo e immettere il codice seguente. Questo codice crea un Windows Forms Application che Scarica l'assembly ClickOnceLibrary quando è necessario.  
  
     [!code-csharp[ClickOnceOnDemandCmdLine#1](../snippets/csharp/VS_Snippets_Winforms/ClickOnceOnDemandCmdLine/CS/Form1.cs#1)]
     [!code-vb[ClickOnceOnDemandCmdLine#1](../snippets/visualbasic/VS_Snippets_Winforms/ClickOnceOnDemandCmdLine/VB/Form1.vb#1)]  
  
10. Nel codice individuare la chiamata a <xref:System.Reflection.Assembly.LoadFile%2A> .  
  
11. Impostare sul `PublicKeyToken` valore recuperato in precedenza.  
  
12. Salvare il file come `Form1.cs` o `Form1.vb` .  
  
13. Compilarlo in un file eseguibile usando il comando seguente.  
  
    ```csharp  
    csc /target:exe /reference:ClickOnceLibrary.dll Form1.cs  
    ```  
  
    ```vb  
    vbc /target:exe /reference:ClickOnceLibrary.dll Form1.vb  
    ```  
  
## <a name="marking-assemblies-as-optional"></a>Contrassegnare gli assembly come facoltativi  
  
#### <a name="to-mark-assemblies-as-optional-in-your-clickonce-application-by-using-mageuiexe"></a>Per contrassegnare gli assembly come facoltativi nell'applicazione ClickOnce usando MageUI.exe  
  
1. Utilizzando MageUI.exe, creare un manifesto dell'applicazione come descritto in [procedura dettagliata: distribuzione manuale di un'applicazione ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md). Usare le impostazioni seguenti per il manifesto dell'applicazione:  
  
    - Denominare il manifesto dell'applicazione `ClickOnceOnDemand` .  
  
    - Nella riga ClickOnceLibrary.dll della pagina **file** impostare la colonna **tipo di file** su **nessuno**.  
  
    - Nella riga ClickOnceLibrary.dll della pagina **file** Digitare `ClickOnceLibrary.dll` nella colonna **gruppo** .  
  
2. Utilizzando MageUI.exe, creare un manifesto di distribuzione come descritto in [procedura dettagliata: distribuzione manuale di un'applicazione ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md). Usare le impostazioni seguenti per il manifesto di distribuzione:  
  
    - Denominare il manifesto della distribuzione `ClickOnceOnDemand` .  
  
## <a name="testing-the-new-assembly"></a>Test del nuovo assembly  
  
#### <a name="to-test-your-on-demand-assembly"></a>Per testare l'assembly su richiesta  
  
1. Caricare la [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] distribuzione in un server Web.  
  
2. Avviare l'applicazione distribuita con [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] da un Web browser immettendo l'URL del manifesto di distribuzione. Se si chiama l' [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] applicazione `ClickOnceOnDemand` e la si carica nella directory radice di adatum.com, l'URL avrà un aspetto simile al seguente:  
  
    ```  
    http://www.adatum.com/ClickOnceOnDemand/ClickOnceOnDemand.application  
    ```  
  
3. Quando viene visualizzato il modulo principale, premere l'oggetto <xref:System.Windows.Forms.Button>. Verrà visualizzata una stringa in una finestra di messaggio con il testo "Hello, World!".  
  
## <a name="see-also"></a>Vedere anche  
 <xref:System.Deployment.Application.ApplicationDeployment>

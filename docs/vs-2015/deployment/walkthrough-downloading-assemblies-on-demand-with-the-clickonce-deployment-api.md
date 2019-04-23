---
title: "Procedura dettagliata: Download di assembly su richiesta con l'API della distribuzione ClickOnce | Microsoft Docs"
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
ms.openlocfilehash: 55dfa9a360d33a73b6298f186d12810f8510b1fc
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2019
ms.locfileid: "60063556"
---
# <a name="walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api"></a>Procedura dettagliata: Download di assembly su richiesta con l'API della distribuzione ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Per impostazione predefinita, tutti gli assembly inclusi un [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] applicazione vengono scaricati alla prima esecuzione dell'applicazione. Tuttavia, è possibile parti dell'applicazione usati da un set ridotto di utenti. In questo caso, è consigliabile scaricare un assembly solo quando si crea uno dei relativi tipi. La procedura dettagliata riportata di seguito illustra come contrassegnare come "facoltativi" determinati assembly nell'applicazione e come scaricarli tramite le classi nello spazio dei nomi <xref:System.Deployment.Application> quando sono richiesti da Common Language Runtime (CLR).  
  
> [!NOTE]
>  Per usare questa procedura, è necessario eseguire l'applicazione con attendibilità totale.  
  
## <a name="prerequisites"></a>Prerequisiti  
 È necessario uno dei componenti seguenti per completare questa procedura dettagliata:  
  
- Il Windows SDK. il SDK di Windows può essere scaricato dal Microsoft Download Center.  
  
- Visual Studio.  
  
## <a name="creating-the-projects"></a>Creazione dei progetti  
  
#### <a name="to-create-a-project-that-uses-an-on-demand-assembly"></a>Per creare un progetto che usa un assembly su richiesta  
  
1. Creare una directory denominata ClickOnceOnDemand.  
  
2. Aprire il prompt dei comandi di Windows SDK o [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] prompt dei comandi.  
  
3. Passare alla directory ClickOnceOnDemand.  
  
4. Generare una coppia di chiavi pubblica/privata usando il comando seguente:  
  
    ```  
    sn -k TestKey.snk  
    ```  
  
5. Utilizzando blocco note o un altro editor di testo, definire una classe denominata `DynamicClass` con una singola proprietà denominata `Message`.  
  
     [!code-csharp[ClickOnceLibrary#1](../snippets/csharp/VS_Snippets_Winforms/ClickOnceLibrary/CS/Class1.cs#1)]
     [!code-vb[ClickOnceLibrary#1](../snippets/visualbasic/VS_Snippets_Winforms/ClickOnceLibrary/VB/Class1.vb#1)]  
  
6. Salvare il testo in un file denominato `ClickOnceLibrary.cs` o `ClickOnceLibrary.vb`, a seconda del linguaggio utilizzato, nella directory ClickOnceOnDemand.  
  
7. Compilare il file in un assembly.  
  
    ```csharp  
    csc /target:library /keyfile:TestKey.snk ClickOnceLibrary.cs  
    ```  
  
    ```vb  
    vbc /target:library /keyfile:TestKey.snk ClickOnceLibrary.vb  
    ```  
  
8. Per ottenere token di chiave pubblica dell'assembly, usare il comando seguente:  
  
    ```  
    sn -T ClickOnceLibrary.dll  
    ```  
  
9. Creare un nuovo file utilizzando il testo dell'editor e immettere il codice seguente. Questo codice crea un'applicazione Windows Form che consente di scaricare l'assembly ClickOnceLibrary quando necessario.  
  
     [!code-csharp[ClickOnceOnDemandCmdLine#1](../snippets/csharp/VS_Snippets_Winforms/ClickOnceOnDemandCmdLine/CS/Form1.cs#1)]
     [!code-vb[ClickOnceOnDemandCmdLine#1](../snippets/visualbasic/VS_Snippets_Winforms/ClickOnceOnDemandCmdLine/VB/Form1.vb#1)]  
  
10. Nel codice, individuare la chiamata a <xref:System.Reflection.Assembly.LoadFile%2A>.  
  
11. Impostare`PublicKeyToken` sul valore recuperato in precedenza.  
  
12. Salvare il file come `Form1.cs` o `Form1.vb`.  
  
13. Compilarla in un eseguibile usando il comando seguente.  
  
    ```csharp  
    csc /target:exe /reference:ClickOnceLibrary.dll Form1.cs  
    ```  
  
    ```vb  
    vbc /target:exe /reference:ClickOnceLibrary.dll Form1.vb  
    ```  
  
## <a name="marking-assemblies-as-optional"></a>Contrassegnare gli assembly come facoltativi  
  
#### <a name="to-mark-assemblies-as-optional-in-your-clickonce-application-by-using-mageuiexe"></a>Per contrassegnare gli assembly come facoltativi nell'applicazione ClickOnce mediante MageUI.exe  
  
1. Usando MageUI.exe, creare un manifesto dell'applicazione come descritto in [procedura dettagliata: Distribuzione manuale di un'applicazione ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md). Usare le impostazioni seguenti per il manifesto dell'applicazione:  
  
    - Nome del manifesto dell'applicazione `ClickOnceOnDemand`.  
  
    - Nel **file** pagina, nella riga ClickOnceLibrary. dll, imposta il **tipo di File** colonna **None**.  
  
    - Nel **file** pagina, nella riga ClickOnceLibrary. dll, digitare `ClickOnceLibrary.dll` nel **gruppo** colonna.  
  
2. Usando MageUI.exe, creare un manifesto di distribuzione come descritto in [procedura dettagliata: Distribuzione manuale di un'applicazione ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md). Usare le impostazioni seguenti per il manifesto di distribuzione:  
  
    - Nome del manifesto di distribuzione `ClickOnceOnDemand`.  
  
## <a name="testing-the-new-assembly"></a>Test del nuovo assembly  
  
#### <a name="to-test-your-on-demand-assembly"></a>Per testare l'assembly su richiesta  
  
1. Caricare il [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] distribuzione a un server Web.  
  
2. Avviare l'applicazione distribuita con [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] da un Web browser immettendo l'URL del manifesto di distribuzione. Se si chiama il [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] applicazione `ClickOnceOnDemand`e caricarlo nella directory radice di adatum.com, l'URL sarà analogo al seguente:  
  
    ```  
    http://www.adatum.com/ClickOnceOnDemand/ClickOnceOnDemand.application  
    ```  
  
3. Quando viene visualizzato il modulo principale, premere l'oggetto <xref:System.Windows.Forms.Button>. Verrà visualizzata una stringa in una finestra di messaggio con il testo "Hello, World!".  
  
## <a name="see-also"></a>Vedere anche  
 <xref:System.Deployment.Application.ApplicationDeployment>

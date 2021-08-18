---
title: Scaricare assembly su richiesta (ClickOnce API)
description: Informazioni su come contrassegnare alcuni assembly nell'applicazione ClickOnce come facoltativi e scaricarli quando common language runtime ne ha bisogno.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
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
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-deployment
ms.workload:
- multiple
ms.openlocfilehash: 046d6932e1bfcbc6f0a4b3c60fab96806b4473fd
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122112256"
---
# <a name="walkthrough-download-assemblies-on-demand-with-the-clickonce-deployment-api"></a>Procedura dettagliata: Scaricare assembly su richiesta con l'API ClickOnce di distribuzione
Per impostazione predefinita, tutti gli assembly inclusi in un'applicazione vengono scaricati alla prima [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] esecuzione dell'applicazione. Tuttavia, è possibile che alcune parti dell'applicazione siano usate da un piccolo set di utenti. In questo caso, è consigliabile scaricare un assembly solo quando si crea uno dei relativi tipi. La procedura dettagliata riportata di seguito illustra come contrassegnare come "facoltativi" determinati assembly nell'applicazione e come scaricarli tramite le classi nello spazio dei nomi <xref:System.Deployment.Application> quando sono richiesti da Common Language Runtime (CLR).

> [!NOTE]
> Per usare questa procedura, è necessario eseguire l'applicazione con attendibilità totale.

## <a name="prerequisites"></a>Prerequisiti
 Per completare questa procedura dettagliata, è necessario uno dei componenti seguenti:

- L Windows SDK. L Windows SDK può essere scaricato dall'Area download Microsoft.

- Visual Studio.

## <a name="create-the-projects"></a>Creare i progetti

#### <a name="to-create-a-project-that-uses-an-on-demand-assembly"></a>Per creare un progetto che usa un assembly su richiesta

1. Creare una directory denominata ClickOnceOnDemand.

2. Aprire il prompt dei Windows SDK o il [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] prompt dei comandi.

3. Passare alla directory ClickOnceOnDemand.

4. Generare una coppia di chiavi pubblica/privata usando il comando seguente:

   ```cmd
   sn -k TestKey.snk
   ```

5. Usando Blocco note o un altro editor di testo, definire una classe denominata `DynamicClass` con una singola proprietà denominata `Message` .

    :::code language="vb" source="../snippets/visualbasic/VS_Snippets_Winforms/ClickOnceLibrary/VB/Class1.vb" id="Snippet1":::
    :::code language="csharp" source="../snippets/csharp/VS_Snippets_Winforms/ClickOnceLibrary/CS/Class1.cs" id="Snippet1":::

6. Salvare il testo come file denominato *ClickOnceLibrary.cs* o *ClickOnceLibrary.vb,* a seconda del linguaggio in uso, nella directory *ClickOnceOnDemand.*

7. Compilare il file in un assembly.

   ```csharp
   csc /target:library /keyfile:TestKey.snk ClickOnceLibrary.cs
   ```

   ```vb
   vbc /target:library /keyfile:TestKey.snk ClickOnceLibrary.vb
   ```

8. Per ottenere il token di chiave pubblica per l'assembly, usare il comando seguente:

   ```cmd
   sn -T ClickOnceLibrary.dll
   ```

9. Creare un nuovo file usando l'editor di testo e immettere il codice seguente. Questo codice crea un'Windows Forms che scarica l'assembly ClickOnceLibrary quando è necessario.

    :::code language="csharp" source="../snippets/csharp/VS_Snippets_Winforms/ClickOnceOnDemandCmdLine/CS/Form1.cs" id="Snippet1":::
    :::code language="vb" source="../snippets/visualbasic/VS_Snippets_Winforms/ClickOnceOnDemandCmdLine/VB/Form1.vb" id="Snippet1":::

10. Nel codice individuare la chiamata a <xref:System.Reflection.Assembly.LoadFile%2A> .

11. Impostare `PublicKeyToken` sul valore recuperato in precedenza.

12. Salvare il file come *Form1.cs* o *Form1.vb*.

13. Compilarlo in un file eseguibile usando il comando seguente.

    ```csharp
    csc /target:exe /reference:ClickOnceLibrary.dll Form1.cs
    ```

    ```vb
    vbc /target:exe /reference:ClickOnceLibrary.dll Form1.vb
    ```

## <a name="mark-assemblies-as-optional"></a>Contrassegnare gli assembly come facoltativi

#### <a name="to-mark-assemblies-as-optional-in-your-clickonce-application-by-using-mageuiexe"></a>Per contrassegnare gli assembly come facoltativi nell'applicazione ClickOnce usando MageUI.exe

1. Usando *MageUI.exe*, creare un manifesto dell'applicazione come descritto in Procedura dettagliata: Distribuire [manualmente un ClickOnce app.](../deployment/walkthrough-manually-deploying-a-clickonce-application.md) Usare le impostazioni seguenti per il manifesto dell'applicazione:

    - Assegnare al manifesto dell'applicazione il nome `ClickOnceOnDemand` .

    - Nella pagina **File,** nella riga *ClickOnceLibrary.dll,* impostare la colonna **Tipo file** su **Nessuno**.

    - Nella **pagina File,** nella riga *ClickOnceLibrary.dll,* `ClickOnceLibrary.dll` digitare nella **colonna** Gruppo.

2. Usando *MageUI.exe*, creare un manifesto di distribuzione come descritto in [Procedura dettagliata: Distribuire manualmente un ClickOnce app.](../deployment/walkthrough-manually-deploying-a-clickonce-application.md) Usare le impostazioni seguenti per il manifesto della distribuzione:

    - Assegnare al manifesto della distribuzione il nome `ClickOnceOnDemand` .

## <a name="testing-the-new-assembly"></a>Test del nuovo assembly

#### <a name="to-test-your-on-demand-assembly"></a>Per testare l'assembly su richiesta

1. Upload la [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] distribuzione in un server Web.

2. Avviare l'applicazione distribuita [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] con da un Web browser immettendo l'URL del manifesto della distribuzione. Se si chiama l'applicazione e la si carica nella directory radice di [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] `ClickOnceOnDemand` adatum.com, l'URL sarà simile al seguente:

   ```
   http://www.adatum.com/ClickOnceOnDemand/ClickOnceOnDemand.application
   ```

3. Quando viene visualizzato il modulo principale, premere l'oggetto <xref:System.Windows.Forms.Button>. Verrà visualizzata una stringa in una finestra di messaggio con il testo "Hello, World!".

## <a name="see-also"></a>Vedere anche
- <xref:System.Deployment.Application.ApplicationDeployment>
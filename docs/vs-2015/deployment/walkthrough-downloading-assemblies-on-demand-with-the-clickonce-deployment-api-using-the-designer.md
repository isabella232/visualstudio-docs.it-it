---
title: "Procedura dettagliata: Download di assembly su richiesta con l'API usando la finestra di progettazione della distribuzione ClickOnce | Microsoft Docs"
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
- Windows applications, ClickOnce deployments
- ClickOnce deployment, on-demand download
- on-demand assemblies, ClickOnce
ms.assetid: 59a0dd5f-1cab-4f2f-b780-0ab7399905d5
caps.latest.revision: 20
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: a7ff4fe24720f707c8f3faa330f71a8abda3c698
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/15/2019
ms.locfileid: "65686342"
---
# <a name="walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer"></a>Procedura dettagliata: Download di assembly su richiesta con l'API di distribuzione ClickOnce tramite la finestra di progettazione
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Per impostazione predefinita, tutti gli assembly inclusi in un'applicazione [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] vengono scaricati alla prima esecuzione dell'applicazione. Alcune parti dell'applicazione possono tuttavia essere usate da un set limitato di utenti. In questo caso, è consigliabile scaricare un assembly solo quando si crea uno dei relativi tipi. La procedura dettagliata riportata di seguito illustra come contrassegnare come "facoltativi" determinati assembly nell'applicazione e come scaricarli tramite le classi nello spazio dei nomi <xref:System.Deployment.Application> quando sono richiesti da Common Language Runtime.  
  
> [!NOTE]
> Per usare questa procedura, è necessario eseguire l'applicazione con attendibilità totale.  
  
> [!NOTE]
> Le finestre di dialogo e i comandi di menu visualizzati potrebbero essere diversi da quelli descritti nella Guida a seconda delle impostazioni attive o dell'edizione del programma. Per modificare le impostazioni, scegliere **Importa/Esporta impostazioni** dal menu **Strumenti** . Per altre informazioni, vedere [Personalizzazione delle impostazioni di sviluppo in Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## <a name="creating-the-projects"></a>Creazione dei progetti  
  
#### <a name="to-create-a-project-that-uses-an-on-demand-assembly-with-visual-studio"></a>Per creare un progetto che usa un assembly su richiesta con Visual Studio  
  
1. Creare un nuovo progetto Windows Form in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Scegliere **Aggiungi** dal menu **File**e quindi fare clic su **Nuovo progetto**. Scegliere un progetto **Libreria di classi** nella finestra di dialogo e assegnare il nome `ClickOnceLibrary`a tale progetto.  
  
    > [!NOTE]
    > In Visual Basic è consigliabile modificare le proprietà del progetto per cambiare lo spazio dei nomi radice per questo progetto in `Microsoft.Samples.ClickOnceOnDemand` o in uno spazio dei nomi selezionato. Per semplicità, i due progetti in questa procedura dettagliata si trovano nello stesso spazio dei nomi.  
  
2. Definire una classe denominata `DynamicClass` con una singola proprietà denominata `Message`.  
  
     [!code-csharp[ClickOnceLibrary#1](../snippets/csharp/VS_Snippets_Winforms/ClickOnceLibrary/CS/Class1.cs#1)]
     [!code-vb[ClickOnceLibrary#1](../snippets/visualbasic/VS_Snippets_Winforms/ClickOnceLibrary/VB/Class1.vb#1)]  
  
3. Selezionare il progetto Windows Forms in **Esplora soluzioni**. Aggiungere un riferimento all'assembly <xref:System.Deployment.Application> e un riferimento al progetto `ClickOnceLibrary` .  
  
    > [!NOTE]
    > In Visual Basic è consigliabile modificare le proprietà del progetto per cambiare lo spazio dei nomi radice per questo progetto in `Microsoft.Samples.ClickOnceOnDemand` o in uno spazio dei nomi selezionato. Per semplicità, i due progetti in questa procedura dettagliata si trovano nello stesso spazio dei nomi.  
  
4. Fare clic con il pulsante destro del mouse sul modulo, scegliere **Visualizza codice** dal menu e aggiungere i riferimenti seguenti al modulo.  
  
     [!code-csharp[ClickOnceOnDemand#1](../snippets/csharp/VS_Snippets_Winforms/ClickOnceOnDemand/CS/Form1.cs#1)]
     [!code-vb[ClickOnceOnDemand#1](../snippets/visualbasic/VS_Snippets_Winforms/ClickOnceOnDemand/VB/Form1.vb#1)]  
  
5. Aggiungere il codice seguente per scaricare l'assembly su richiesta. Questo codice illustra come eseguire il mapping di un set di assembly in un nome di gruppo che usa una classe <xref:System.Collections.DictionaryBase.Dictionary%2A> generica. In questa procedura dettagliata viene scaricato un singolo assembly, pertanto è presente un solo assembly nel gruppo. In un'applicazione reale è in genere consigliabile scaricare contemporaneamente tutti gli assembly relativi a una singola funzionalità dell'applicazione. La tabella di mapping consente di eseguire facilmente questa operazione associando tutte le DLL che appartengono a una funzionalità al nome di un gruppo di download.  
  
     [!code-csharp[ClickOnceOnDemand#2](../snippets/csharp/VS_Snippets_Winforms/ClickOnceOnDemand/CS/Form1.cs#2)]
     [!code-vb[ClickOnceOnDemand#2](../snippets/visualbasic/VS_Snippets_Winforms/ClickOnceOnDemand/VB/Form1.vb#2)]  
  
6. Scegliere **Casella degli strumenti** dal menu **Visualizza**. Trascinare un elemento <xref:System.Windows.Forms.Button> dalla **Casella degli strumenti** nel modulo. Fare doppio clic sul pulsante e aggiungere il codice seguente al gestore dell'evento <xref:System.Windows.Forms.Control.Click> .  
  
     [!code-csharp[ClickOnceOnDemand#3](../snippets/csharp/VS_Snippets_Winforms/ClickOnceOnDemand/CS/Form1.cs#3)]
     [!code-vb[ClickOnceOnDemand#3](../snippets/visualbasic/VS_Snippets_Winforms/ClickOnceOnDemand/VB/Form1.vb#3)]  
  
## <a name="marking-assemblies-as-optional"></a>Contrassegnare gli assembly come facoltativi  
  
#### <a name="to-mark-assemblies-as-optional-in-your-clickonce-application-by-using-visual-studio"></a>Per contrassegnare gli assembly come facoltativi nell'applicazione ClickOnce mediante Visual Studio  
  
1. Fare clic con il pulsante destro del mouse sul progetto Windows Forms in **Esplora soluzioni** e scegliere **Proprietà**. Selezionare la scheda **Pubblica** .  
  
2. Fare clic sul pulsante **File applicazione** .  
  
3. Trovare l'elenco per ClickOnceLibrary.dll. Impostare la casella di riepilogo a discesa **Stato pubblicazione** su **Includi**.  
  
4. Espandere la casella di riepilogo a discesa **Gruppo** e selezionare **Nuovo**. Immettere il nome `ClickOnceLibrary` come nome del nuovo gruppo.  
  
5. Continuare a pubblicare l'applicazione come descritto in [come: Pubblicare un'applicazione ClickOnce mediante la Pubblicazione guidata](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md).  
  
#### <a name="to-mark-assemblies-as-optional-in-your-clickonce-application-by-using-manifest-generation-and-editing-tool--graphical-client-mageuiexe"></a>Per contrassegnare gli assembly come facoltativi nell'applicazione ClickOnce mediante lo Strumento per la generazione e la modifica di manifesti - Client grafico (MageUI.exe)  
  
1. Creare le [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] manifesti come descritto in [procedura dettagliata: Distribuzione manuale di un'applicazione ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md).  
  
2. Prima di chiudere MageUI.exe, selezionare la scheda contenente il manifesto dell'applicazione di distribuzione e all'interno della scheda selezionare la scheda **File** .  
  
3. Trovare ClickOnceLibrary.dll nell'elenco dei file dell'applicazione e impostare la relativa colonna **Tipo di file** su **Nessuno**. Per la colonna **Gruppo** digitare `ClickOnceLibrary.dll`.  
  
## <a name="testing-the-new-assembly"></a>Test del nuovo assembly  
  
#### <a name="to-test-your-on-demand-assembly"></a>Per testare l'assembly su richiesta  
  
1. Avviare l'applicazione distribuita con [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)].  
  
2. Quando viene visualizzato il modulo principale, premere l'oggetto <xref:System.Windows.Forms.Button>. Verrà visualizzata una stringa in una finestra di messaggio con il testo "Hello, World!"  
  
## <a name="see-also"></a>Vedere anche  
 <xref:System.Deployment.Application.ApplicationDeployment>

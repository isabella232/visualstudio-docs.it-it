---
title: 'Procedura: Creare un controllo della casella degli strumenti che usa Windows Form | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- Toolbox control
- winforms
- toolbox
ms.assetid: abbd3c3c-3a6e-4539-bd6c-a5891dead234
caps.latest.revision: 12
manager: jillfra
ms.openlocfilehash: 7bb327ff7cd3909e4d860203322a9b72aa71fbf3
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2019
ms.locfileid: "59001434"
---
# <a name="how-to-create-a-toolbox-control-that-uses-windows-forms"></a>Procedura: Creare un controllo della casella degli strumenti che usa Windows Form
Il modello di controllo della casella degli strumenti Windows Form incluso in [!INCLUDE[vssdk_dev11_long](../includes/vssdk-dev11-long-md.md)] consente di creare controlli Windows Form che vengono aggiunti automaticamente alla **casella degli strumenti** quando l'estensione viene installata. Questo argomento mostra come usare il modello per creare un controllo della **casella degli strumenti** che è possibile distribuire ad altri utenti.  
  
> [!NOTE]
>  Per informazioni su come scaricare Visual Studio SDK, vedere il [centro per sviluppatori per l'estensione dell'IDE di Visual Studio](http://go.microsoft.com/fwlink/?linkid=121964) nel sito Web MSDN.  
  
## <a name="creating-a-toolbox-control"></a>Creazione di un controllo della casella degli strumenti  
 Usare il modello di controllo della casella degli strumenti Windows Form per creare il progetto e quindi compilare un'interfaccia utente nella finestra di progettazione.  
  
#### <a name="to-create-a-windows-forms-toolbox-control-project"></a>Per creare un progetto di controllo della casella degli strumenti Windows Form  
  
1.  Scegliere **Nuovo** dal menu **File**, quindi fare clic su **Progetto**.  
  
2.  Nella finestra di dialogo **Nuovo progetto** fare clic sul nodo per il linguaggio di programmazione preferito in **Modelli installati**e quindi selezionare **Extensibility**. Nell'elenco dei tipi di progetto selezionare **Controllo della casella degli strumenti Windows Forms**.  
  
3.  Nella casella **Nome** digitare il nome da usare per il progetto. Fare clic su **OK**.  
  
     Visual Studio crea una soluzione contenente un controllo utente, un attributo per inserire il controllo nella **casella degli strumenti**e un manifesto VSIX per la distribuzione.  
  
#### <a name="to-build-the-control-ui"></a>Per compilare l'interfaccia utente del controllo  
  
1.  In **Esplora soluzioni**fare doppio clic sul file ToolboxControl.cs per aprirlo nella finestra di progettazione.  
  
2.  Dalla **casella degli strumenti**trascinare tutti i controlli che si vuole aggiungere nell'area di progettazione e disporli in base alla progettazione.  
  
3.  Nella finestra **Proprietà** impostare le proprietà pubbliche nel controllo utente e nei controlli figlio.  
  
## <a name="coding-the-control"></a>Codifica del controllo  
 Per impostazione predefinita, il controllo verrà visualizzato nella **casella degli strumenti** come **ToolboxControl1** in un gruppo di elementi della **casella degli strumenti** che ha lo stesso nome della soluzione. È possibile modificare questi nomi nel file ToolboxControl.cs.  
  
#### <a name="to-code-the-control"></a>Per codificare il controllo  
  
1.  In **Esplora soluzioni**fare clic con il pulsante destro del mouse su ToolboxControl.cs e quindi scegliere **Visualizza codice** per aprire il file in visualizzazione Codice.  
  
2.  Nella definizione della classe parziale che implementa il controllo fare clic con il pulsante destro del mouse sul nome della classe, scegliere **Refactoring**e quindi fare clic su **Rinomina**. Modificare il nome della classe specificando il nome che dovrà essere visualizzato nella **casella degli strumenti** quando il controllo verrà installato.  
  
3.  Immediatamente sopra la definizione della classe, nella dichiarazione dell'attributo `ProvideToolboxControl` , modificare il valore del primo parametro specificando il nome del gruppo di elementi che ospiteranno il controllo nella **casella degli strumenti**.  
  
     L'esempio seguente mostra l'attributo `ProvideToolboxControl` e la definizione di classe modificata per un controllo chiamato `Counter` nel gruppo di elementi `General` .  
  
     [!code-csharp[ToolboxControlWinForms#07](../snippets/csharp/VS_Snippets_VSSDK/toolboxcontrolwinforms/cs/toolboxcontrol.cs#07)]  
  
4.  Implementare le proprietà, i metodi e gli eventi per il controllo.  
  
## <a name="building-testing-and-deployment"></a>Compilazione, testing e distribuzione  
 Se si preme F5, viene compilato il progetto, che include un file di distribuzione VSIX, e viene aperta una seconda istanza di Visual Studio con il controllo installato nella **casella degli strumenti**.  
  
#### <a name="to-build-and-test-the-control"></a>Per compilare e testare il controllo  
  
1.  Premere F5.  
  
2.  Nella nuova istanza di Visual Studio creare un progetto Windows Forms Application.  
  
3.  Individuare il controllo nella **casella degli strumenti** e trascinarlo nell'area di progettazione.  
  
4.  Nella finestra **Proprietà** verificare che le proprietà siano visualizzate nel modo previsto.  
  
5.  Aggiungere eventuale codice o altri controlli necessari per testare i metodi e gli eventi.  
  
6.  Premere F5 per aprire Windows Forms Application.  
  
7.  Verificare che le proprietà, i metodi e gli eventi del controllo si comportino nel modo previsto.  
  
#### <a name="to-deploy-the-control"></a>Per distribuire il controllo  
  
1.  Dopo aver compilato il progetto testato, aprire la cartella \bin\debug\ del progetto in Esplora file e individuare il file VSIX.  
  
2.  Caricare il file VSIX in una rete o in un sito Web.  
  
     Se si carica il file per il [Visual Studio Marketplace](https://marketplace.visualstudio.com/) sito Web, altri utenti potranno usare **gestore estensioni del** in Visual Studio per trovare il controllo e installarlo.  
  
## <a name="see-also"></a>Vedere anche  
 [Creazione di un controllo della casella degli strumenti WPF](../extensibility/creating-a-wpf-toolbox-control.md)
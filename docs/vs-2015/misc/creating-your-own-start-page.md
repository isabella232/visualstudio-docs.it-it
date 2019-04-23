---
title: Creare una pagina di avvio | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- Create start page
- custom start page
- customize start page
ms.assetid: a0df5b9c-0932-4e54-86f0-28530ad9d684
caps.latest.revision: 22
manager: jillfra
ms.openlocfilehash: 662ee0ba4659e09b02f120bac5b3eaa728add6d9
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2019
ms.locfileid: "60037895"
---
# <a name="creating-your-own-start-page"></a>Creazione di una pagina iniziale personalizzata
È possibile creare una pagina iniziale personalizzata usando il modello di progetto di pagina iniziale o creando una pagina iniziale vuota.  
  
 La finestra di progettazione XAML potrebbe non fornire rappresentazioni visive completamente accurate delle pagine iniziali personalizzate a causa delle dipendenze dal modello applicativo di Visual Studio.  
  
## <a name="using-the-project-template"></a>Uso del modello di progetto  
 Il modello di progetto di pagina iniziale crea un progetto di pagina iniziale che è una copia completa della pagina iniziale di Visual Studio. È quindi possibile modificare la pagina iniziale in base alle specifiche.  
  
#### <a name="to-create-a-custom-start-page-by-using-the-start-page-project-template"></a>Per creare una pagina iniziale personalizzata con il modello di progetto di pagina iniziale  
  
1. Scaricare e installare il [modello di progetto di pagina iniziale](http://go.microsoft.com/fwlink/?LinkId=186204) da Visual Studio Gallery.  
  
    > [!WARNING]
    >  A questo punto il modello di progetto di pagina iniziale di Visual Studio 2010 non è ancora aggiornato. Per informazioni su come aggiornare il modello, vedere [come: Aggiornare una pagina iniziale personalizzata di Visual Studio](../misc/how-to-upgrade-a-visual-studio-custom-start-page.md).  
  
2. Dopo aver installato il modello, usarlo per creare un nuovo progetto di pagina iniziale.  
  
3. In **Modelli installati**nel riquadro sinistro della finestra di dialogo Nuovo progetto espandere il nodo **Altri tipi di progetto** e quindi fare clic sul nodo **Extensibility**.  
  
4. Nel riquadro centrale fare clic su **Personalizza pagina iniziale**, assegnare un nome al progetto e quindi fare clic su **OK**.  
  
     Viene creato un progetto di pagina iniziale che è una copia completa della pagina iniziale di Visual Studio.  
  
5. Da **Esplora soluzioni**aprire il file **StartPage.xaml**.  
  
6. Modificare il file StartPage.xaml.  
  
     È possibile visualizzare il proprio lavoro premendo F5 per aprire un'istanza sperimentale di Visual Studio con la pagina iniziale personalizzata installata.  
  
## <a name="creating-a-blank-start-page"></a>Creazione di una pagina iniziale vuota  
 Il metodo più semplice per creare una pagina iniziale vuota è usare il modello di progetto di pagina iniziale e quindi rimuovere il contenuto.  
  
#### <a name="to-create-a-blank-start-page-by-using-the-start-page-project-template"></a>Per creare una pagina iniziale vuota con il modello di progetto di pagina iniziale  
  
1. Creare un progetto di pagina iniziale usando il modello di progetto di pagina iniziale, come descritto nella routine precedente.  
  
2. Aprire il file StartPage.xaml.  
  
3. Rimuovere tutto il contenuto della pagina, lasciando solo gli elementi XML esterni e l'elemento griglia <xref:System.Windows.Controls.Grid> contenitore, in modo che il file XAML assomigli a quello nell'esempio seguente.  
  
   ```xaml
      <Grid xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
                xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
                xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006" 
                xmlns:d="http://schemas.microsoft.com/expression/blend/2008" 
                xmlns:sp="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.StartPage"
                xmlns:vs="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.10.0"
                xmlns:vsfx="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.10.0"
            mc:Ignorable="d" 
                d:DesignHeight="600" d:DesignWidth="800">
       <Grid>
           <!--Add content here.-->
       </Grid>
   </Grid>
   ```
      
4. Rimuovere tutti i file di supporto che non si intende usare.  
  
    Mantenere i file VSIX e PKGDEF per scopi di distribuzione.  
  
   In alternativa, è possibile creare una pagina iniziale vuota creando un file XAML con la struttura di tag corretta perché venga riconosciuta da Visual Studio. È quindi possibile aggiungere il markup e il code-behind per ottenere la funzionalità e l'aspetto desiderati. Per altre informazioni, vedere [creazione di una pagina iniziale personalizzata](../extensibility/creating-a-custom-start-page.md).  
  
## <a name="testing-and-applying-the-custom-start-page"></a>Testing e applicazione della pagina iniziale personalizzata  
 Non impostare l'istanza primaria per l'esecuzione della pagina iniziale personalizzata fino a quando non si verifica che questa non si arresta in modo anomalo. Una volta testata la pagina iniziale personalizzata, è possibile applicarla nel sistema ripetendo gli ultimi tre passaggi di questa routine nell'istanza primaria di Visual Studio.  
  
#### <a name="to-test-a-custom-start-page"></a>Per testare una pagina iniziale personalizzata  
  
1. Premere F5.  
  
    L'istanza sperimentale di Visual Studio viene aperta con la nuova pagina iniziale installata, ma non selezionata.  
  
2. Nell'istanza sperimentale di Visual Studio scegliere **Opzioni** dal menu **Strumenti**.  
  
3. Nella finestra di dialogo **Opzioni** selezionare **Avvio**in **Ambiente**. Nell'elenco **Personalizza pagina iniziale** selezionare quindi il file XAML e fare clic su **OK**.  
  
4. Scegliere **Pagina iniziale** dal menu **Visualizza**.  
  
    Verrà visualizzata la pagina iniziale funzionante. È necessario chiudere l'istanza sperimentale, copiare di nuovo tutti i file modificati e quindi riaprire l'istanza sperimentale per visualizzare le nuove modifiche.  
  
   È possibile condividere la pagina iniziale personalizzata caricando il file VSIX dalla directory bin\debug nel [Visual Studio Marketplace](https://marketplace.visualstudio.com/) sito Web o in un altro sito Web o rete intranet condivisione. Per altre informazioni, vedere [Deploying Custom Start Pages](../extensibility/deploying-custom-start-pages.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Personalizzazione della pagina iniziale](../ide/customizing-the-start-page-for-visual-studio.md)   
 [Procedura dettagliata: Aggiunta di XAML personalizzato nella pagina iniziale](../extensibility/walkthrough-adding-custom-xaml-to-the-start-page.md)
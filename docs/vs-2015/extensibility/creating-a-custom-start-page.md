---
title: Pagina iniziale di creazione di un oggetto personalizzato | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d67e0c53-9f5a-45fb-a929-b9d2125c3c82
caps.latest.revision: 19
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 052f05c3485e9ecdfbfe74b6a142c44c7b0699ff
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49239785"
---
# <a name="creating-a-custom-start-page"></a>Creazione di una pagina iniziale personalizzata
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Se non è possibile creare una pagina iniziale personalizzata usando il modello di progetto di pagina iniziale, come descritto in [pagine iniziali](../misc/creating-your-own-start-page.md), è possibile creare manualmente una seguendo i passaggi descritti in questo documento.  
  
## <a name="creating-a-blank-start-page"></a>Creazione di una pagina iniziale vuota  
 Assicurarsi prima di tutto una pagina iniziale vuota creando un file con estensione XAML che ha una struttura di tag che verranno riconosciute dallo Visual Studio. Aggiungere quindi il markup e code-behind per produrre l'aspetto e funzionalità che si desidera.  
  
#### <a name="to-create-a-blank-start-page"></a>Per creare una pagina iniziale vuota  
  
1.  Creare un nuovo progetto di tipo **applicazione WPF** (**Visual c# / Desktop Windows**.  
  
2.  Aggiungere un riferimento a `Microsoft.VisualStudio.Shell.14.0`.  
  
3.  Aprire il file XAML nell'editor XML e cambiare il livello superiore \<finestra > elemento da un \<UserControl > elemento senza rimuovere una delle dichiarazioni dello spazio dei nomi.  
  
4.  Rimuovere il `x:Class` dichiarazione di elemento di primo livello. In questo modo il contenuto XAML compatibile con la finestra degli strumenti di Visual Studio che ospita la pagina iniziale.  
  
5.  Aggiungere le seguenti dichiarazioni dello spazio dei nomi di livello principale \<UserControl > elemento.  
  
    ```  
    xmlns:vs="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.14.0"  
    xmlns:vsfx="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.14.0"  
    ```  
  
     Questi spazi dei nomi consentono di accedere ai comandi di Visual Studio, controlli e le impostazioni dell'interfaccia utente. Per altre informazioni, vedere [aggiunta di comandi di Visual Studio a una pagina iniziale](../extensibility/adding-visual-studio-commands-to-a-start-page.md).  
  
     Nell'esempio seguente viene illustrato il markup nel file con estensione XAML per una pagina iniziale vuota. Qualsiasi contenuto personalizzato devono essere inseriti in interna <xref:System.Windows.Controls.Grid> elemento.  
  
    ```vb  
    <UserControl  
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
        xmlns:d="http://schemas.microsoft.com/expression/blend/2008"  
        xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"  
        xmlns:MyNamespace="clr-namespace:ManualStartPage;assembly=ManualStartPage"  
        xmlns:vs="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.14.0"  
                xmlns:vsfx="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.14.0"  
        xmlns:local="clr-namespace:StartPageHost"  
        mc:Ignorable="d"  
         Height="350" Width="525">  
        <Grid>  
        <!--Add content here.-->  
        </Grid>  
    </UserControl>  
    ```  
  
6.  Aggiungere controlli a vuoto \<UserControl > elemento per riempire la pagina iniziale personalizzata. Per informazioni su come aggiungere funzionalità specifiche per Visual Studio, vedere [aggiunta di comandi di Visual Studio a una pagina iniziale](../extensibility/adding-visual-studio-commands-to-a-start-page.md).  
  
## <a name="testing-and-applying-the-custom-start-page"></a>Testing e applicazione della pagina iniziale personalizzata  
 Non impostare l'istanza primaria di Visual Studio per l'esecuzione della pagina iniziale personalizzata fino a quando non si verifica che causa l'arresto anomalo Visual Studio. Al contrario, testarla nell'istanza sperimentale.  
  
#### <a name="to-test-a-manually-created-custom-start-page"></a>Per testare una pagina di avvio personalizzata creata manualmente  
  
1.  Copiare il file XAML e qualsiasi file di testo o markup supporto file, per il **%USERPROFILE%\My Documents\Visual Studio 2015\StartPages\\**  cartella.  
  
2.  Se la pagina iniziale di fa riferimento a tutti i controlli o i tipi negli assembly che non sono installati da Visual Studio, copiare gli assembly e quindi incollarli nella _cartella di installazione di Visual Studio_**\Common7\IDE\ PrivateAssemblies\\**.  
  
3.  Un prompt dei comandi di Visual Studio, digitare **devenv /rootsuffix Exp** per aprire un'istanza sperimentale di Visual Studio.  
  
4.  Nell'istanza sperimentale, passare al **Strumenti / opzioni / ambiente / avvio** pagina e selezionare il file XAML dalle **Personalizza pagina iniziale** elenco a discesa.  
  
5.  Scegliere **Pagina iniziale** dal menu **Visualizza**.  
  
     La pagina iniziale personalizzata deve essere visualizzata. Se si desidera modificare tutti i file, è necessario chiudere l'istanza sperimentale, apportare le modifiche, copiare e incollare i file modificati e quindi aprire nuovamente l'istanza sperimentale per visualizzare le modifiche.  
  
#### <a name="to-apply-the-custom-start-page-in-the-primary-instance-of-visual-studio"></a>Per applicare la pagina personalizzata iniziale nell'istanza primaria di Visual Studio  
  
-   Dopo avere testato la pagina iniziale e ha rilevato che è stabile, usare il **Personalizza pagina iniziale** opzione il **opzioni** finestra di dialogo per selezionarla come pagina iniziale nell'istanza primaria di Visual Studio  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura dettagliata: Aggiunta di XAML personalizzato nella pagina iniziale](../extensibility/walkthrough-adding-custom-xaml-to-the-start-page.md)   
 [Aggiunta di controllo utente alla pagina iniziale](../extensibility/adding-user-control-to-the-start-page.md)   
 [Aggiunta di comandi di Visual Studio a una pagina iniziale](../extensibility/adding-visual-studio-commands-to-a-start-page.md)   
 [Procedura dettagliata: Salvataggio delle impostazioni utente a una pagina iniziale](../extensibility/walkthrough-saving-user-settings-on-a-start-page.md)   
 [Distribuzione di pagine iniziali personalizzate](../extensibility/deploying-custom-start-pages.md)


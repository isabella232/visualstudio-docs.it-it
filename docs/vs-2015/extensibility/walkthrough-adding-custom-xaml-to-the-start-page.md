---
title: 'Procedura dettagliata: Aggiunta di XAML personalizzato nella pagina iniziale | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- custom start page
- xaml start page
ms.assetid: 9af4d5f9-1cfc-4221-aea7-c8cd3f7571a6
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 796beda7675d45698dd361e09f5b27e54d8b5da6
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47532527"
---
# <a name="walkthrough-adding-custom-xaml-to-the-start-page"></a>Procedura dettagliata: aggiunta di codice XAML personalizzato nella pagina iniziale
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [procedura dettagliata: aggiunta di XAML personalizzato nella pagina iniziale](https://docs.microsoft.com/visualstudio/extensibility/walkthrough-adding-custom-xaml-to-the-start-page).  
  
Questa procedura dettagliata viene illustrato come creare una pagina iniziale personalizzata di Visual Studio che contiene un Web browser.  
  
## <a name="adding-custom-xaml"></a>XAML personalizzata aggiunta  
  
1.  Creare una pagina iniziale, seguendo le istruzioni in [creazione di una pagina iniziale personalizzata](../extensibility/creating-a-custom-start-page.md).  
  
2.  Nel file MainWindow. XAML, individuare il \<griglia > sezione.  
  
3.  Aggiungere un \<TabControl > elemento e un \<TabItem > all'interno di \< griglia > elemento, come illustrato nell'esempio seguente.  
  
    ```xml  
    <Grid>  
        <TabControl>  
            <TabItem Header="Bing" Height="Auto">  
                <Frame Source="http://www.bing.com" />  
            </TabItem>  
        </TabControl>  
    </Grid>  
    ```  
  
4.  Aggiungere una seconda \<TabItem >, con un \<pulsante > elemento che si apre un nuovo progetto:  
  
    ```xml  
    <Grid>  
        <TabControl>  
            <TabItem Header="MyButton" Height="Auto">  
                <Button Name="btnNewProj" Content="New Project"   
                    Command="{x:Static vscom:VSCommands.ExecuteCommand}"  
                    CommandParameter="File.NewProject" >  
                </Button>  
            </TabItem>  
            <TabItem Header="Bing" Height="Auto">  
                <Frame Source="http://www.bing.com" />  
            </TabItem>  
        </TabControl>  
    </Grid>  
    ```  
  
## <a name="testing-the-custom-start-page"></a>Test della pagina iniziale personalizzata  
  
1.  Premere F5.  
  
     Si apre l'istanza sperimentale di Visual Studio, con la pagina iniziale personalizzata installata ma non è selezionata.  
  
2.  Nell'istanza sperimentale di Visual Studio, aprire il **Strumenti/opzioni / ambiente** pagina.  
  
3.  Selezionare **avvio**. Nel **Personalizza pagina iniziale** elencare, selezionare il file con estensione XAML e fare clic su **OK**.  
  
4.  Scegliere **Pagina iniziale** dal menu **Visualizza**.  
  
5.  Scegliere il **Bing** scheda.  
  
     Si verrà visualizzata una pagina web di Bing.  
  
6.  Scegliere il **MyButton** scheda.  
  
     Dovrebbe essere un **MyProject** button, che consente di visualizzare i **nuovo progetto** finestra di dialogo.  
  
7.  Chiudere l'istanza sperimentale.  
  
## <a name="applying-the-custom-start-page"></a>Applicare la pagina iniziale personalizzata  
  
#### <a name="to-test-the-custom-start-page"></a>Per testare la pagina iniziale personalizzata  
  
1.  Nelle **Strumenti / opzioni / ambiente**, selezionare **avvio**. Nel **Personalizza pagina iniziale** elencare, selezionare il file con estensione XAML e fare clic su **OK**.  
  
## <a name="next-steps"></a>Passaggi successivi  
 La pagina iniziale di Visual Studio contiene ora una scheda che visualizza una scheda del browser Web e una scheda MyButton. È possibile creare pagine iniziali personalizzate che dispongono di altre funzionalità tramite il *code-behind* model per aggiungere un file dll personalizzato, come illustrato [aggiunta controllo utente alla pagina avvio](../extensibility/adding-user-control-to-the-start-page.md). È possibile condividere le pagine iniziali personalizzate con altri utenti di pubblicazione del file con estensione VSIX risultante per il [Visual Studio Gallery](http://go.microsoft.com/fwlink/?LinkID=123847) sito Web o in un altro sito Web o rete una condivisione. Per altre informazioni, vedere [Deploying Custom Start Pages](../extensibility/deploying-custom-start-pages.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Personalizzazione della pagina iniziale](../ide/customizing-the-start-page-for-visual-studio.md)   
 [Controlli contenitore WPF](http://msdn.microsoft.com/en-us/a0177167-d7db-4205-9607-8ae316952566)

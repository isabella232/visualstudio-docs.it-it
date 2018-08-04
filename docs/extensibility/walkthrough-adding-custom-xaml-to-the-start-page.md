---
title: 'Procedura dettagliata: Aggiunta di XAML personalizzato nella pagina iniziale | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- custom start page
- xaml start page
ms.assetid: 9af4d5f9-1cfc-4221-aea7-c8cd3f7571a6
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 85a462501637fab8ea916dd5488b0796351164d5
ms.sourcegitcommit: 1c2ed640512ba613b3bbbc9ce348e28be6ca3e45
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/03/2018
ms.locfileid: "39500709"
---
# <a name="walkthrough-add-custom-xaml-to-the-start-page"></a>Procedura dettagliata: Aggiungere XAML personalizzato nella pagina iniziale
Questa procedura dettagliata viene illustrato come creare una pagina iniziale personalizzata di Visual Studio che contiene un Web browser.  
  
## <a name="adding-custom-xaml"></a>XAML personalizzata aggiunta  
  
1.  Creare una pagina iniziale, seguendo le istruzioni in [creare una pagina iniziale personalizzata](../extensibility/creating-a-custom-start-page.md).  
  
2.  Nel *MainWindow. XAML* del file, trovare il \<griglia > sezione.  
  
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
  
1.  Premere **F5**.  
  
     Si apre l'istanza sperimentale di Visual Studio, con la pagina iniziale personalizzata installata ma non è selezionata.  
  
2.  Nell'istanza sperimentale di Visual Studio, aprire il **Strumenti/opzioni / ambiente** pagina.  
  
3.  Selezionare **avvio**. Nel **Personalizza pagina iniziale** elenco, selezionare la *XAML* file e fare clic su **OK**.  
  
4.  Scegliere **Pagina iniziale** dal menu **Visualizza**.  
  
5.  Scegliere il **Bing** scheda.  
  
     Si verrà visualizzata una pagina web di Bing.  
  
6.  Scegliere il **MyButton** scheda.  
  
     Dovrebbe essere un **MyProject** button, che consente di visualizzare i **nuovo progetto** finestra di dialogo.  
  
7.  Chiudere l'istanza sperimentale.  
  
## <a name="apply-the-custom-start-page"></a>Applicare la pagina iniziale personalizzata  
  
### <a name="to-test-the-custom-start-page"></a>Per testare la pagina iniziale personalizzata  
  
1.  Nelle **Strumenti / opzioni / ambiente**, selezionare **avvio**. Nel **Personalizza pagina iniziale** elenco, selezionare la *XAML* file e fare clic su **OK**.  
  
## <a name="next-steps"></a>Passaggi successivi  
 La pagina iniziale di Visual Studio contiene ora una scheda che visualizza una scheda del browser Web e una scheda MyButton. È possibile creare pagine iniziali personalizzate che dispongono di altre funzionalità tramite il *code-behind* model per aggiungere un file dll personalizzato, come illustrato [aggiunta controllo utente alla pagina avvio](../extensibility/adding-user-control-to-the-start-page.md). È possibile condividere le pagine iniziali personalizzate con altri utenti di pubblicazione del file con estensione VSIX risultante per il [Visual Studio Gallery](http://go.microsoft.com/fwlink/?LinkID=123847) sito Web o in un altro sito Web o rete una condivisione. Per altre informazioni, vedere [Deploying Custom Start Pages](../extensibility/deploying-custom-start-pages.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Personalizzare la pagina iniziale](../ide/customizing-the-start-page-for-visual-studio.md)   
 [Controlli contenitore WPF](http://msdn.microsoft.com/en-us/a0177167-d7db-4205-9607-8ae316952566)
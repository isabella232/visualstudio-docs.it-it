---
title: 'Procedura dettagliata: aggiunta di codice XAML personalizzato alla pagina iniziale | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- custom start page
- xaml start page
ms.assetid: 9af4d5f9-1cfc-4221-aea7-c8cd3f7571a6
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 7b2de492bd1eddf4bf18e4824cdb64de4241fa5f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "65674119"
---
# <a name="walkthrough-adding-custom-xaml-to-the-start-page"></a>Procedura dettagliata: aggiunta di codice XAML personalizzato nella pagina iniziale
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Questa procedura dettagliata illustra come creare una pagina iniziale personalizzata di Visual Studio contenente un Web browser.  
  
## <a name="adding-custom-xaml"></a>Aggiunta di XAML personalizzato  
  
1. Creare una pagina iniziale seguendo le istruzioni riportate in [creazione di una pagina iniziale personalizzata](../extensibility/creating-a-custom-start-page.md).  
  
2. Nel file MainWindow. XAML trovare la \<Grid> sezione.  
  
3. Aggiungere un \<TabControl> elemento e un oggetto \<TabItem> all'interno dell' \< Grid> elemento, come illustrato nell'esempio seguente.  
  
    ```xml  
    <Grid>  
        <TabControl>  
            <TabItem Header="Bing" Height="Auto">  
                <Frame Source="http://www.bing.com" />  
            </TabItem>  
        </TabControl>  
    </Grid>  
    ```  
  
4. Aggiungere un secondo \<TabItem> con un \<Button> elemento che apre un nuovo progetto:  
  
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
  
1. Premere F5.  
  
     Si apre l'istanza sperimentale di Visual Studio, con la pagina iniziale personalizzata installata, ma non selezionata.  
  
2. Nell'istanza sperimentale di Visual Studio aprire la pagina **strumenti/Options/ambiente** .  
  
3. Selezionare **Startup (avvio**). Nell'elenco **Personalizza pagina iniziale** selezionare il file XAML e fare clic su **OK**.  
  
4. Scegliere **Pagina iniziale** dal menu **Visualizza**.  
  
5. Fare clic sulla scheda **Bing** .  
  
     Verrà visualizzata una pagina Web di Bing.  
  
6. Fare clic sulla scheda **MyButton** .  
  
     Verrà visualizzato il pulsante **progetto** , che consente di aprire la finestra di dialogo **nuovo progetto** .  
  
7. Chiudere l'istanza sperimentale.  
  
## <a name="applying-the-custom-start-page"></a>Applicazione della pagina iniziale personalizzata  
  
#### <a name="to-test-the-custom-start-page"></a>Per eseguire il test della pagina iniziale personalizzata  
  
1. In **strumenti/opzioni/ambiente**selezionare **Startup (avvio**). Nell'elenco **Personalizza pagina iniziale** selezionare il file XAML e fare clic su **OK**.  
  
## <a name="next-steps"></a>Passaggi successivi  
 La pagina iniziale di Visual Studio contiene ora una scheda che consente di visualizzare una scheda Web browser e una scheda pulsante. È possibile creare pagine iniziali personalizzate con altre funzionalità usando il modello *code-behind* per aggiungere un file con estensione dll personalizzato, come illustrato in [aggiunta del controllo utente alla pagina iniziale](../extensibility/adding-user-control-to-the-start-page.md). È possibile condividere le pagine iniziali personalizzate con altri utenti pubblicando il file con estensione VSIX risultante nel sito Web [Visual Studio Marketplace](https://marketplace.visualstudio.com/) o in un altro sito Web o in una condivisione di rete. Per altre informazioni, vedere [Deploying Custom Start Pages](../extensibility/deploying-custom-start-pages.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Personalizzazione della pagina iniziale](../ide/customizing-the-start-page-for-visual-studio.md)   
 [Controlli contenitore WPF](https://msdn.microsoft.com/a0177167-d7db-4205-9607-8ae316952566)

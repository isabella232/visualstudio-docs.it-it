---
title: 'Procedura dettagliata: Aggiunta di XAML personalizzato nella pagina iniziale | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- custom start page
- xaml start page
ms.assetid: 9af4d5f9-1cfc-4221-aea7-c8cd3f7571a6
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
monikerRange: vs-2017
ms.openlocfilehash: 992937ea0c90e3734a38ba6f2e56b19918fd7375
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/22/2019
ms.locfileid: "56709174"
---
# <a name="walkthrough-add-custom-xaml-to-the-start-page"></a>Procedura dettagliata: Aggiungere XAML personalizzato nella pagina iniziale

Questa procedura dettagliata viene illustrato come creare una pagina di avvio personalizzata di Visual Studio che contiene un Web browser.

## <a name="add-custom-xaml"></a>Aggiungere XAML personalizzato

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

## <a name="test-the-custom-start-page"></a>Testare la pagina iniziale personalizzata

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

Per applicare la pagina iniziale personalizzata, in **degli strumenti** > **opzioni** > **ambiente**selezionare **avvio**. Nel **Personalizza pagina iniziale** elenco, selezionare la *XAML* file e fare clic su **OK**.

## <a name="next-steps"></a>Passaggi successivi

La pagina iniziale di Visual Studio contiene ora una scheda che visualizza una scheda del browser Web e una scheda MyButton. È possibile creare pagine iniziali personalizzate che dispongono di altre funzionalità tramite il *code-behind* model per aggiungere un file dll personalizzato, come illustrato [aggiunta controllo utente alla pagina avvio](../extensibility/adding-user-control-to-the-start-page.md). È possibile condividere pagine iniziali personalizzate con altri utenti di pubblicazione del file con estensione VSIX risultante per il [Visual Studio Gallery](http://go.microsoft.com/fwlink/?LinkID=123847) sito Web o in un altro sito Web o rete una condivisione. Per altre informazioni, vedere [Deploying Custom Start Pages](../extensibility/deploying-custom-start-pages.md).

## <a name="see-also"></a>Vedere anche

- [Personalizzare la pagina iniziale](../ide/customizing-the-start-page-for-visual-studio.md)
- [Controlli contenitore WPF](https://msdn.microsoft.com/library/a0177167-d7db-4205-9607-8ae316952566)
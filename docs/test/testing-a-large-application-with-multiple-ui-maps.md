---
title: Testare un'applicazione di grandi dimensioni con più mappe dell'interfaccia utente
description: Informazioni su come usare i test codificati dell'interfaccia utente quando si testa un'applicazione di grandi dimensioni usando più test dell'interfaccia Mappe. Questa funzionalità richiede Visual Studio Enterprise.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- coded UI tests, multiple UI maps
- coded UI tests, for large applications
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-test
ms.workload:
- multiple
ms.openlocfilehash: 5bd5762c72b3ef99d7e58a7ea8b99621f555212393d9b7fa87a877b068c6dc34
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121352357"
---
# <a name="test-a-large-application-with-multiple-ui-maps"></a>Testare un'applicazione di grandi dimensioni con più mappe dell'interfaccia utente

In questo argomento viene illustrato l'uso dei test codificati dell'interfaccia utente per il test di un'applicazione di grandi dimensioni con più mappe dell'interfaccia utente.

[!INCLUDE [coded-ui-test-deprecation](includes/coded-ui-test-deprecation.md)]

**Requisiti**

- Visual Studio Enterprise

Quando si crea un nuovo test codificato dell'interfaccia utente, per impostazione predefinita il framework di test di Visual Studio genera il codice per il test in una classe [UIMap](/previous-versions/dd580454(v=vs.140)). Per altre informazioni sulla registrazione di test codificati dell'interfaccia utente, vedere [Creare test codificati dell'interfaccia utente](../test/use-ui-automation-to-test-your-code.md) e [Composizione di un test codificato dell'interfaccia utente](../test/anatomy-of-a-coded-ui-test.md).

Il codice generato per la mappa dell'interfaccia utente contiene una classe per ogni oggetto con cui il test interagisce. Per ogni metodo generato, viene generata una classe complementare per i parametri del metodo appositamente per quel metodo. Se l'applicazione contiene un numero elevato di oggetti, pagine, moduli e controlli, la mappa dell'interfaccia utente può raggiungere dimensioni significative. Inoltre, se più persone stanno operando sui test, l'applicazione può diventare difficile da gestire se è presente un solo file di mappa dell'interfaccia utente di grandi dimensioni.

L'uso di più file di mappa dell'interfaccia utente può offrire i vantaggi seguenti:

- Ogni mappa può essere associata a un subset logico dell'applicazione per semplificare la gestione delle modifiche.

- Ogni tester può operare su una sezione dell'applicazione e archiviare il proprio codice senza interferire con altri tester che lavorano su altre sezioni dell'applicazione.

- Le aggiunte all'interfaccia utente dell'applicazione possono essere ridimensionate in modo incrementale con effetti minimi sui test per le altre parti dell'interfaccia utente.

## <a name="do-you-need-multiple-ui-maps"></a>Situazioni in cui sono necessarie più mappe dell'interfaccia utente
Creare più mappe dell'interfaccia utente nei tipi di situazioni seguenti:

- Diversi set complessi di controlli dell'interfaccia utente compositi che insieme eseguono un'operazione logica, ad esempio una pagina di registrazione in un sito Web o la pagina di acquisto di un carrello.

- Un set indipendente di controlli a cui si accede da vari punti dell'applicazione, ad esempio una procedura guidata con numerose pagine di operazioni. Se le pagine di una procedura guidata sono particolarmente complesse, è possibile creare mappe dell'interfaccia utente separate per ogni pagina.

## <a name="add-multiple-ui-maps"></a>Aggiungere più mappe dell'interfaccia utente

### <a name="to-add-a-ui-map-to-your-coded-ui-test-project"></a>Per aggiungere una mappa dell'interfaccia utente al progetto di test codificato dell'interfaccia utente

1. Per creare una cartella nel progetto di test codificato dell'interfaccia utente in cui archiviare tutte le mappe dell'interfaccia utente, in **Esplora soluzioni** fare clic con il pulsante destro del mouse sul file del progetto di test codificato dell'interfaccia utente, scegliere **Aggiungi** e quindi **Nuova cartella**. Ad esempio, la cartella potrebbe essere denominata `UIMaps`.

    La nuova cartella verrà visualizzata sotto il progetto di test codificato dell'interfaccia utente.

2. Fare clic con il pulsante destro del sulla cartella `UIMaps`, scegliere **Aggiungi** e quindi **Nuovo elemento**.

    La finestra di dialogo **Aggiungi nuovo elemento** viene visualizzata.

   > [!NOTE]
   > È necessario essere all'interno di un progetto di test codificato dell'interfaccia utente per aggiungere una nuova mappa di test codificati dell'interfaccia utente.

3. Selezionare **Mappa di test codificati dell'interfaccia utente** nell'elenco.

    Nella casella **Nome** immettere un nome per la nuova mappa dell'interfaccia utente. Usare il nome del componente o della pagina che verrà rappresentata dalla mappa, ad esempio `HomePageMap`.

4. Scegliere **Aggiungi**.

    La finestra di Visual Studio viene ridotta a icona e viene visualizzata la finestra di dialogo **Generatore di test codificati dell'interfaccia utente**.

5. Registrare le azioni per il primo metodo e scegliere **Genera codice**.

6. Dopo avere registrato tutte le azioni e le asserzioni per il primo componente o pagina e averli raggruppati in metodi, chiudere la finestra di dialogo **Generatore di test codificati dell'interfaccia utente**.

7. Continuare a creare le mappe dell'interfaccia utente. Registrare le azioni e le asserzioni, raggrupparle in metodi per ogni componente e quindi generare il codice.

   In molti casi la finestra di primo livello dell'applicazione rimane costante per tutte le procedure guidate, i moduli e le pagine. Anche se ogni mappa dell'interfaccia utente ha una classe per la finestra di primo livello, è probabile che tutte le mappe facciano riferimento alla stessa finestra di primo livello, in cui vengono eseguiti tutti i componenti dell'applicazione. I test codificati dell'interfaccia utente eseguono la ricerca dei controlli in modo gerarchico dall'altro al basso iniziando dalla finestra di primo livello, in modo che in un'applicazione complessa la finestra di primo livello effettiva possa essere duplicata in ogni mappa dell'interfaccia utente. Se la finestra di primo livello effettiva viene duplicata, ogni cambiamento della finestra determina più modifiche. Questo può causare problemi di prestazioni nel passaggio da una mappa dell'interfaccia utente all'altra.

   Per attenuare questo effetto, è possibile usare il metodo `CopyFrom()` per assicurarsi che la nuova finestra di primo livello in quella determinata mappa dell'interfaccia utente corrisponda alla finestra di primo livello principale.

## <a name="example"></a>Esempio

L'esempio seguente fa parte di una classe di utilità che consente l'accesso a ogni componente e ai relativi controlli figlio, rappresentati dalle classi generate nelle varie mappe dell'interfaccia utente.

Per questo esempio, l'applicazione Web denominata `Contoso` include una home page, una pagina dei prodotti e una pagina del carrello. Ognuna di queste pagine condivide una finestra di primo livello che è la finestra del browser. È disponibile una mappa dell'interfaccia utente per ogni pagina e la classe di utilità presenta un codice simile al seguente:

```csharp
using ContosoProject.UIMaps;
using ContosoProject.UIMaps.HomePageClasses;
using ContosoProject.UIMaps.ProductPageClasses;
using ContosoProject.UIMaps.ShoppingCartClasses;

namespace ContosoProject
{
    public class TestRunUtility
    {
        // Private fields for the properties
        private HomePage homePage = null;
        private ProductPage productPage = null;
        private ShoppingCart shoppingCart = null;

        public TestRunUtility()
        {
            homePage = new HomePage();
        }

        // Properties that get each UI Map
        public HomePage HomePage
        {
            get { return homePage; }
            set { homePage = value; }
        }

        // Gets the ProductPage from the ProductPageMap.
        public ProductPage ProductPageObject
        {
            get
            {
                if (productPage == null)
                {
                    // Instantiate a new page from the UI Map classes
                    productPage = new ProductPage();

                    // Since the Product Page and Home Page both use
                    // the same browser page as the top level window,
                    // get the top level window properties from the
                    // Home Page.
                    productPage.UIContosoFinalizeWindow.CopyFrom(
                        HomePage.UIContosoWindowsIWindow);
                }
                return productPage;
            }
        }

    // Continue to create properties for each page, getting the
    // page object from the corresponding UI Map and copying the
    // top level window properties from the Home Page.
}
```

## <a name="see-also"></a>Vedi anche

- [UIMap](/previous-versions/dd580454(v=vs.140))
- <xref:Microsoft.VisualStudio.TestTools.UITesting.BrowserWindow.CopyFrom%2A>
- [Usare l'automazione dell'interfaccia utente per testare il codice](../test/use-ui-automation-to-test-your-code.md)
- [Creare test codificati dell'interfaccia utente](../test/use-ui-automation-to-test-your-code.md)
- [Anatomia di un test codificato dell'interfaccia utente](../test/anatomy-of-a-coded-ui-test.md)

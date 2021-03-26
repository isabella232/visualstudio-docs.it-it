---
title: 'Procedura dettagliata: creazione di un SDK tramite JavaScript | Microsoft Docs'
description: Informazioni su come usare JavaScript per creare un semplice SDK matematico come estensione di Visual Studio usando questa procedura dettagliata.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: a8c89d5d-5b78-4435-817f-c5f25ca6d715
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 3b9a3d9e84731fe0c2526b69f60cdda1b1487583
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105080385"
---
# <a name="walkthrough-create-an-sdk-using-javascript"></a>Procedura dettagliata: creare un SDK usando JavaScript
In questa procedura dettagliata viene illustrato come utilizzare JavaScript per creare un semplice Math SDK come estensione di Visual Studio (VSIX).  La procedura dettagliata è divisa in queste parti:

- [Per creare il progetto SDK dell'estensione SimpleMathVSIX](../extensibility/walkthrough-creating-an-sdk-using-javascript.md#createSimpleMathVSIX)

- [Per creare un'app di esempio che usa l'SDK](../extensibility/walkthrough-creating-an-sdk-using-javascript.md#createSampleApp)

  Per JavaScript non è disponibile alcun tipo di progetto libreria di classi. In questa procedura dettagliata, il file di *arithmetic.js* di esempio viene creato direttamente nel progetto VSIX. In pratica, è consigliabile compilare e testare prima i file JavaScript e CSS come app di Windows Store, ad esempio usando il modello **applicazione vuota** , prima di inserirli in un progetto VSIX.

## <a name="prerequisites"></a>Prerequisiti
 Per seguire questa procedura dettagliata, è necessario installare Visual Studio SDK. Per ulteriori informazioni, vedere [Visual Studio SDK](../extensibility/visual-studio-sdk.md).

## <a name="to-create-the-simplemathvsix-extension-sdk-project"></a><a name="createSimpleMathVSIX"></a> Per creare il progetto SDK dell'estensione SimpleMathVSIX

1. Sulla barra dei menu scegliere **file**  >  **nuovo**  >  **progetto**.

2. Nell'elenco delle categorie di modelli, in **Visual C#**, selezionare **estendibilità**, quindi selezionare il modello di **progetto VSIX** .

3. Nella casella di testo **nome** specificare `SimpleMathVSIX` e scegliere il pulsante **OK** .

4. Se viene visualizzata la **creazione guidata pacchetto di Visual Studio** , fare clic sul pulsante **Avanti** nella pagina **iniziale** , quindi, nella **pagina 1 di 7**, scegliere il pulsante **fine** .

     Sebbene **Progettazione manifesto** venga aperto, questa procedura dettagliata verrà mantenuta semplice modificando direttamente il file manifesto.

5. In **Esplora soluzioni** aprire il menu di scelta rapida per il file **source. Extension. vsixmanifest** , quindi scegliere **Visualizza codice**. Usare questo codice per sostituire il contenuto esistente nel file.

    ```xml
    <?xml version="1.0" encoding="utf-8"?>
    <PackageManifest Version="2.0.0" xmlns="http://schemas.microsoft.com/developer/vsx-schema/2011" xmlns:d="http://schemas.microsoft.com/developer/vsx-schema-design/2011">
      <Metadata>
        <Identity Id="SimpleMathVSIX" Version="1.0" Language="en-US" Publisher="myname" />
        <DisplayName>Simple Math</DisplayName>
        <Description>Does basic arithmetic calculations.</Description>
      </Metadata>
      <Installation Scope="Global" AllUsers="true">
        <InstallationTarget Id="Microsoft.ExtensionSDK" TargetPlatformIdentifier="Windows" TargetPlatformVersion="v8.0" SdkName="SimpleMath" SdkVersion="1.0" />
      </Installation>
      <Dependencies>
        <Dependency Id="Microsoft.Framework.NDP" DisplayName="Microsoft .NET Framework" d:Source="Manual" Version="4.5" />
      </Dependencies>
      <Assets>
        <Asset Type="Microsoft.ExtensionSDK" d:Source="File" Path="SDKManifest.xml" />
      </Assets>
    </PackageManifest>
    ```

6. In **Esplora soluzioni** aprire il menu di scelta rapida per il progetto **SimpleMathVSIX** , quindi scegliere **Aggiungi**  >  **nuovo elemento**.

7. Nella categoria **dati** selezionare **file XML**, assegnare un nome al file `SDKManifest.xml` e scegliere il pulsante **Aggiungi** .

8. In **Esplora soluzioni** aprire il menu di scelta rapida per il file di **SDKManifest.xml** , quindi scegliere **Apri** per visualizzare il file nell' **editor XML**.

9. Aggiungere il codice seguente al file di **SDKManifest.xml** .

    ```xml
    <?xml version="1.0" encoding="utf-8" ?>
    <FileList
      DisplayName="Simple Math"
      MinVSVersion="14.0"
      AppliesTo="JavaScript+WindowsAppContainer"
      SupportsMultipleVersions="Error"
      MoreInfo="https://msdn.microsoft.com/">

      <!-- JS -->
      <File Content="js\arithmetic.js" />
    </FileList>

    ```

10. In **Esplora soluzioni** scegliere **proprietà** dal menu di scelta rapida per il file di **SDKManifest.xml** .

11. Nella finestra **Proprietà** impostare la proprietà **Includi in VSIX** su **true**.

12. In **Esplora soluzioni** scegliere **Aggiungi** nuova cartella dal menu di scelta rapida per il progetto **SimpleMathVSIX**  >  e quindi assegnare un nome alla cartella `Redist` .

13. Aggiungere le sottocartelle in Redist per creare la struttura di cartelle:

     *\Redist\CommonConfiguration\Neutral\SimpleMath\js\\*

14. Nel menu di scelta rapida per la cartella **\js \\** scegliere **Aggiungi**  >  **nuovo elemento**.

15. In **elementi di Visual C#** selezionare la categoria **Web** e quindi selezionare l'elemento **file JavaScript** . Assegnare un nome al file `arithmetic.js` , quindi scegliere il pulsante **Aggiungi** .

16. Inserire il codice seguente in *arithmetic.js*:

    ```csharp
    (function (global) {
        "use strict";
        global.Arithmetic = {
            add: function (firstNumber, secondNumber) {
                return firstNumber + secondNumber;
            },

            subtract: function (firstNumber, secondNumber) {
                return firstNumber - secondNumber;
            },

            multiply: function (firstNumber, secondNumber) {
                return firstNumber * secondNumber;
            },

            divide: function (firstNumber, secondNumber) {
                return firstNumber / secondNumber;
            }
        };
    })(this);

    ```

17. In **Esplora soluzioni** scegliere **proprietà** dal menu di scelta rapida per il file di **arithmetic.js** . Apportare le modifiche seguenti alle proprietà:

    - Impostare la proprietà **Includi in VSIX** su **true**.

    - Impostare la proprietà **copia nella directory di output** su **copia sempre**.

18. In **Esplora soluzioni** scegliere **Compila** dal menu di scelta rapida per il progetto **SimpleMathVSIX** .

19. Una volta completata la compilazione, scegliere **Apri cartella in Esplora file** dal menu di scelta rapida del progetto. Passare a **\bin\Debug \\** ed eseguire `SimpleMathVSIX.vsix` per installarlo.

20. Scegliere il pulsante **Installa** e consentire il completamento dell'installazione.

21. Riavviare Visual Studio.

## <a name="to-create-a-sample-app-that-uses-the-sdk"></a><a name="createSampleApp"></a> Per creare un'app di esempio che usa l'SDK

1. Sulla barra dei menu scegliere **file**  >  **nuovo**  >  **progetto**.

2. Nell'elenco delle categorie di modelli, in **JavaScript** selezionare **Windows Store**, quindi selezionare il modello **applicazione vuota** .

3. Nella casella **nome** specificare `ArithmeticUI` . Fare clic su **OK** .

4. In **Esplora soluzioni** aprire il menu di scelta rapida per il progetto **ArithmeticUI** , quindi scegliere **Aggiungi**  >  **riferimento**.

5. In **Windows** scegliere **estensioni**. si noti che viene visualizzata la **semplice matematica** .

6. Selezionare la casella di controllo **Math semplice** , quindi scegliere il pulsante **OK** .

7. In **Esplora soluzioni**, in **riferimenti**, si noti che viene visualizzato il riferimento **matematico semplice** . Espanderla e notare che è presente una **cartella \\ \js** che include **arithmetic.js**. È possibile aprire **arithmetic.js** per verificare che il codice sorgente sia stato installato.

8. Usare il codice seguente per sostituire il contenuto di *default.htm*.

   ```html
   <!DOCTYPE html>
   <html>
   <head>
       <meta charset="utf-8" />
       <title>ArithmeticUI</title>

       <!-- WinJS references -->
       <link href="//Microsoft.WinJS.1.0/css/ui-dark.css" rel="stylesheet" />
       <script src="//Microsoft.WinJS.1.0/js/base.js"></script>
       <script src="//Microsoft.WinJS.1.0/js/ui.js"></script>

       <!-- ArithmeticUI references -->
       <link href="/css/default.css" rel="stylesheet" />
       <script src="/js/default.js"></script>
       <script src="/SimpleMath/js/arithmetic.js"></script>
   </head>
   <body>
       <form>
       <div id="calculator" class="ms-grid">
           <input name="firstNumber" id="firstNumber" type="number" step="any">
           <div id="operators">
               <button class="operator" type="button">+</button>
               <button class="operator" type="button">-</button>
               <button class="operator" type="button">*</button>
               <button class="operator" type="button">/</button>
           </div>
           <input id="secondNumber" type="number">
           <button class="calculate" type="button">=</button>
           <input id="result" type="number" name="result" disabled="" readonly="">
       </div>
       </form>
   </body>
   </html>
   ```

9. Usare il codice seguente per sostituire il contenuto di *\js\default.js*.

    ```csharp
    (function () {
        "use strict";

        var app = WinJS.Application;
        var operation = null;

        function calculateResult() {
            var firstNumber = parseFloat(document.querySelector("#firstNumber").value),
                secondNumber = parseFloat(document.querySelector("#secondNumber").value),
                result = 0;

            if (isNaN(firstNumber) || isNaN(secondNumber)) {
                result = 0;
            }
            else {
                switch (operation) {
                    case "+":
                        result = Arithmetic.add(firstNumber, secondNumber);
                        break;
                    case "-":
                        result = Arithmetic.subtract(firstNumber, secondNumber);
                        break;
                    case "*":
                        result = Arithmetic.multiply(firstNumber, secondNumber);
                        break;
                    case "/":
                        result = Arithmetic.divide(firstNumber, secondNumber);
                        break;
                    default:
                }
            }
            document.querySelector("#result").value = result.toString();
        }

        app.onactivated = function (args) {
            document.querySelector("#calculator").addEventListener("click", function (event) {
                if (event.target.tagName.toLowerCase() === "button") {
                    switch (event.target.className) {
                        case "operator":
                            operation = event.target.innerText;
                            break;
                        case "calculate":
                            calculateResult();
                            break;
                        default:
                            break;
                    }
                }
            });
        };

        app.start();
    })();
    ```

10. Sostituire il contenuto di *\css\default.CSS* con il codice seguente:

    ```xml
    form {
        display: -ms-grid;
        -ms-grid-rows: 1fr auto 1fr;
        -ms-grid-columns: 1fr auto 1fr;
        height: 100%;
        width: 100%;
    }

    button, input[type=number] {
        margin-right: 5px;
        -ms-grid-row-align: center;
    }

    #calculator {
        -ms-grid-column: 2;
        -ms-grid-row: 2;
        display: -ms-grid;
        -ms-grid-rows: 1fr;
        -ms-grid-columns: auto min-content auto auto auto;
    }

    .ms-grid input {
        width: 5em;
    }

    #firstNumber {
        -ms-grid-column: 1;
        -ms-grid-row-align: center;
    }

    #operators {
        -ms-grid-column: 2;
        -ms-grid-row-align: center;
    }

        #operators button.operator {
            margin-bottom: 5px;
            height: 40px;
        }

    #secondNumber {
        -ms-grid-column: 3;
    }

    button.calculate {
        -ms-grid-column: 4;
        -ms-grid-row-align: center;
        height: 40px;
    }

    #result {
        -ms-grid-column: 5;
    }

    ```

11. Premere il tasto **F5** per compilare ed eseguire l'app.

12. Nell'interfaccia utente dell'app immettere due numeri, selezionare un'operazione, quindi scegliere il **=** pulsante. Viene visualizzato il risultato corretto.

## <a name="see-also"></a>Vedi anche
- [Creare un Software Development Kit](../extensibility/creating-a-software-development-kit.md)

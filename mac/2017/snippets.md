---
title: Frammenti di codice
description: Come usare i frammenti di codice per programmare in modo efficiente in Visual Studio per Mac
author: heiligerdankgesang
ms.author: dominicn
ms.date: 02/07/2019
ms.assetid: 0FE27C0C-A861-4133-A74E-8D0505CF5342
ms.openlocfilehash: 96344b72dd27095f8b9060078112fb767b1338fc
ms.sourcegitcommit: 0841d3f610bd2af4af1cf07dd9d31d1e0629b193
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/09/2021
ms.locfileid: "123961991"
---
# <a name="code-snippets"></a>Frammenti di codice

I frammenti di codice, a volte indicati come _modelli di codice_, sono utili per una programmazione efficiente poiché consentono di inserire e modificare blocchi di testo scritti in precedenza. L'uso di frammenti di codice può essere comodo per aggiungere rapidamente modelli comuni o anche per apprendere nuovi modelli, nel caso lo sviluppatore non sia sicuro della sintassi. Sono disponibili modelli per C#, F#, HTML, XML, Python e Razor.

Questa sezione illustra come creare, inserire e usare frammenti nel codice.

## <a name="inserting-a-snippet"></a>Inserimento di un frammento

Vi sono diversi modi per aggiungere frammenti di codice, alcuni dei quali sono descritti di seguito:

- **Espansione tramite TAB** &ndash; Iniziare a digitare il nome del modello, selezionarlo nell'elenco e quindi premere **TAB**, **TAB** per aggiungerlo:

  ![Espansione tramite TAB nel codice](media/source-editor-image13.png)

- **Casella degli strumenti** &ndash; Usare il riquadro della casella degli strumenti per visualizzare un elenco di tutti i frammenti di codice. Trascinare il modello desiderato dalla casella degli strumenti nella posizione corretta nel codice sorgente:

  [![Frammenti di codice nella casella degli strumenti](media/source-editor-image14-sml.png)](media/source-editor-image14.png#lightbox)

- **Comando di inserimento modelli** &ndash; Attualmente non è presente un tasto di scelta rapida predefinito per inserire un modello. Per crearne uno, spostarsi su **Visual Studio > Preferenze > Tasti di scelta rapida** e cercare `template`. In questo modo è possibile aggiungere il tasto di scelta rapida desiderato nel campo Modifica tasto di scelta rapida e quindi fare clic su **Applica**:

  ![Comando di inserimento modello](media/source-editor-image15.png)

## <a name="creating-a-new-template"></a>Creazione di un nuovo modello

Sebbene vi siano molti modelli esistenti in una vasta gamma di linguaggi che è possibile usare e modificare, è anche possibile aggiungere nuovi modelli da **Visual Studio > Preferenze > Editor di testo > Frammenti di codice**:

![Inserire un nuovo modello](media/source-editor-image12.png)

Premere i pulsanti **Aggiungi** o **Modifica** per creare o modificare frammenti di codice.

## <a name="keywords-in-code-snippets"></a>Parole chiave nei frammenti di codice

Dopo aver inserito un frammento di codice nell'editor, tutte le parole chiave definite vengono evidenziate e possono essere modificate spostandosi tra di esse con TAB. Le parole chiave si comportano come una "variabile" nel frammento di codice e vengono definite aggiungendo un segno di dollaro `$` prima e dopo il nome della parola chiave. 

La finestra **Modifica modello** è illustrata di seguito e rappresenta la modifica del frammento predefinito `prop`. Il frammento contiene due parole chiave e che possono avere altre proprietà impostate (ad esempio un valore predefinito e una descrizione comando) sul &ndash; `$type$` lato destro della `$name$` &ndash; finestra:

![Finestra Modifica modello](media/source-editor-image12z.png)

Per definire un frammento di codice vengono usati i campi seguenti:

- **Shortcut (Scelta rapida)** &ndash; Il testo digitato dall'utente per inserire il frammento di codice.
- **Group (Gruppo)** &ndash; Usando questo valore i frammenti di codice vengono raggruppati nel menu del contenuto del frammento di codice.
- **Description (Descrizione)** &ndash; Spiegazione dello scopo del frammento di codice.
- **Mime** &ndash; Controlla i tipi di file in cui è disponibile il frammento di codice.
- **Is expandable template (Modello espandibile)** &ndash; Assicurarsi che questa casella di controllo sia selezionata in modo che il frammento di codice possa essere inserito in corrispondenza del cursore digitando la scelta rapida.
- **Is surround with template (Racchiudi tra con modello)** &ndash; Selezionare questa opzione per visualizzare la scelta rapida nel menu di scelta rapida **Racchiudi tra** nell'editor.
- **Template text (Testo del modello)** &ndash; Il frammento di codice effettivo che verrà inserito nell'editor. I segnaposto per le parole chiave possono essere definiti racchiudendo un token tra segni di dollaro, ad esempio `$type$`.
- **Pannello delle proprietà delle parole chiave** &ndash; Sul lato destro della finestra, usare l'elenco a discesa in alto per scegliere una parola chiave (ad esempio `type`) e modificare proprietà come il valore predefinito e la descrizione comando.

## <a name="using-keywords-in-the-editor"></a>Uso delle parole chiave nell'editor

Per usare un frammento di codice con parole chiave, come quello definito in precedenza, digitare la scelta rapida e premere **TAB** due volte. Il contenuto del frammento di codice verrà inserito in corrispondenza del cursore:

![Frammento di codice inserito con le parole chiave visualizzate](media/source-editor-image12a.png)

Premere **TAB** per spostarsi tra `object` e `MyProperty` per personalizzare il frammento di codice per la classe.

Una parola chiave può essere ripetuta in un frammento di codice, come in questo esempio `for`. Si noti che la parola chiave `$i$` compare 3 volte:

![Modello di frammento di codice con le parole chiave ripetute](media/source-editor-image12b.png)

Quando viene usato nell'editor, il tasto **TAB** consentirà di spostarsi tra il primo `i` e `max`. Se si sovrascrive `i` con un nome di variabile diverso, verranno aggiornate tutte e tre le istanze:

![Frammento di codice inserito che mostra più parole chiave](media/source-editor-image12c.png)

### <a name="reserved-keywords"></a>Parole chiave riservate

Sono disponibili due parole chiave riservate che è possibile usare in un frammento di codice:

- `$selected$` &ndash; Se per il frammento di codice è selezionata l'opzione **Is surround with template** (Racchiudi tra con modello), questa parola chiave verrà sostituita dal testo che era evidenziato nell'editor quando è stato scelto il frammento di codice.
- `$end$`Quando l'utente ha terminato di modificare le parole chiave in un frammento di codice, il cursore verrà posizionato &ndash; in corrispondenza della posizione della parola chiave `$end$` .

Il frammento di codice `for` nella sezione precedente è un esempio di entrambe queste parole chiave riservate.

Per altri dettagli, vedere le [informazioni di riferimento sui frammenti di codice di Visual Studio](/visualstudio/ide/code-snippets-schema-reference#keywords).

## <a name="see-also"></a>Vedi anche

- [Frammenti di codice (Visual Studio in Windows)](/visualstudio/ide/code-snippets)
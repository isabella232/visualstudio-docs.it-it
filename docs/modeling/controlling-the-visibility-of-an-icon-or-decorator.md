---
title: Controllo della visibilità di un'icona o di un elemento Decorator
description: Informazioni su come controllare la visibilità di un'icona o di un elemento Decorator a seconda dello stato delle proprietà nel modello.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.technology: vs-ide-modeling
ms.workload:
- multiple
ms.openlocfilehash: 54dd15b59628883d42f28ab9988ae75d0c7bbd52
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122061363"
---
# <a name="controlling-the-visibility-of-an-icon-or-decorator"></a>Controllo della visibilità di un'icona o di un elemento Decorator
Un *elemento Decorator* è un'icona o una riga di testo visualizzata in una forma in un linguaggio specifico di dominio (DSL). È possibile fare in modo che l'elemento Decorator venga visualizzato e scompare a seconda dello stato delle proprietà nel modello. Ad esempio, in una forma che rappresenta una persona, è possibile che vengano visualizzate icone diverse a seconda del sesso della persona, del numero di figli e così via.

## <a name="controlling-the-visibility-of-an-icon-or-decorator"></a>Controllo della visibilità di un'icona o di un elemento Decorator
 Nella procedura seguente si presuppone che sia già stata definita una forma e il relativo mapping a una classe di dominio. Per altre informazioni, vedere [How to Define a Domain-Specific Language](../modeling/how-to-define-a-domain-specific-language.md).

#### <a name="to-control-the-visibility-of-an-icon-or-text-decorator"></a>Per controllare la visibilità di un'icona o di un elemento Decorator di testo

1. Nel diagramma di definizione DSL aggiungere alla classe shape le icone o gli elementi Decorator di testo da visualizzare.

   1. Fare clic con il pulsante destro del mouse sulla classe shape, scegliere **Aggiungi** e quindi fare clic sul tipo di elemento Decorator richiesto.

   2. Impostare la proprietà **Position dell'elemento Decorator.** Più elementi Decorator possono avere la stessa posizione. Ad esempio, è possibile avere icone per il maschio e la femmina che condividono la stessa posizione.

   3. Impostare la **proprietà Icona** predefinita di un elemento Decorator icona.

2. Selezionare la mappa degli elementi del diagramma, ovvero la linea grigia tra la classe shape e la classe di dominio nel diagramma di definizione DSL.

3. Nella finestra Dettagli DSL, nella scheda **Decorator Mappe,** selezionare un elemento Decorator. Ad esempio, MaleDecorator.

4. Selezionare la **casella Filtro visibilità.**

5. Se la proprietà di dominio che deve controllare la visibilità si trova nella classe di dominio immediata, lasciare **vuoto Percorso proprietà filtro.**

    In caso contrario, fare clic sul menu a discesa e passare alla relazione o alla classe in cui si trova la proprietà.

   - Per evitare una segnalazione errori, non è consigliabile spostarsi all'interno di una relazione contrassegnata con "*" nello strumento di navigazione.

6. Impostare la **proprietà Filter** su una proprietà di dominio. Ad esempio, Gender.

7. **Nell'elenco Voci di visibilità** aggiungere i valori di questa proprietà di dominio per cui deve essere visibile l'elemento Decorator. Ad esempio, Male.

8. Ripetere i passaggi per ogni icona.

9. **Trasformare tutti i modelli,** compilare ed eseguire e aprire un diagramma di test.

10. Quando si modifica il valore della proprietà di controllo, gli elementi Decorator vengono visualizzati e scompaiono.

    Spesso si vuole che la visibilità sia controllata da una formula più complessa rispetto a un semplice set di valori. Ad esempio, per avere un'icona dipende dal numero di collegamenti di un determinato tipo o per fare in modo che dipersi da un valore che indica se un numero si trova in un intervallo specifico. In tal caso, usare la procedura seguente.

#### <a name="to-control-the-visibility-of-a-decorator-based-on-a-formula"></a>Per controllare la visibilità di un elemento Decorator in base a una formula

1. Aggiungere una proprietà di dominio calcolata alla classe di dominio. Nella finestra **Proprietà** impostare i valori seguenti:

     **IsBrowsable =** `False` **: nasconde la proprietà all'utente**    

     **Kind =** `Calculated` **: ciò significa che si fornirà il codice che calcola il valore**    

     **Nome,** ad esempio **DecoratorControl**

     **digitare** = `Boolean`

     Per altre informazioni, vedere [Calculated and Custom Archiviazione Properties](../modeling/calculated-and-custom-storage-properties.md).

2. Fare in modo che la nuova proprietà controlli la visibilità dell'elemento Decorator.

    1. Selezionare la mappa degli elementi del diagramma, ovvero la linea grigia dalla classe di dominio alla forma. Nella finestra **Dettagli DSL** aprire la scheda **DecoratorMap.**

    2. Selezionare la **casella Filtro visibilità.**

    3. In **Proprietà filtro** selezionare la proprietà del controllo **DecoratorControl**.

    4. In **Voci di visibilità** immettere `True` .

3. Fare **clic su Trasforma tutti i** modelli nella barra **Esplora soluzioni** strumenti.

4. Scegliere **Compila** soluzione **dal** menu Compila.

5. Fare doppio clic sul report degli errori visualizzato: "*YourClass* does not contain a definition for GetDecoratorControlValue ...".

     L'editor di testo viene aperto in Dsl\GeneratedCode\DomainClasses.cs. Sopra l'errore evidenziato è riportato un commento che richiede di aggiungere un metodo.

6. Si noti lo spazio dei nomi, la classe e il metodo mancanti.  Ad esempio, Company.FamilyTree.Person.GetDecoratorControlValue().

7. In un file di codice separato scrivere una definizione di classe parziale contenente il metodo mancante. Esempio:

    ```
    namespace Company.FamilyTree
    { partial class Person
      { bool GetDecoratorControlValue()
        {
          return this.Children.Count > 0;
    } } }
    ```

     Per altre informazioni sulla personalizzazione del modello con il codice del programma, vedere Esplorazione e aggiornamento [di un modello nel codice programma](../modeling/navigating-and-updating-a-model-in-program-code.md).

8. Ricompilare ed eseguire la soluzione.

## <a name="see-also"></a>Vedi anche

- [Definizione di forme e connettori](../modeling/defining-shapes-and-connectors.md)
- [Impostazione di un'immagine di sfondo in un diagramma](../modeling/setting-a-background-image-on-a-diagram.md)
- [Esplorazione e aggiornamento di un modello nel codice del programma](../modeling/navigating-and-updating-a-model-in-program-code.md)
- [Scrittura di codice per personalizzare un linguaggio specifico di dominio](../modeling/writing-code-to-customise-a-domain-specific-language.md)
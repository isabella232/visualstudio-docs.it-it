---
title: Controllo della visibilità di un'icona o di un elemento Decorator | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: 2697fd5d-b936-4b6b-b87b-be64825dc7a4
caps.latest.revision: 4
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 49cecff999e0155209ba58c20c0d623b15d63698
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72667835"
---
# <a name="controlling-the-visibility-of-an-icon-or-decorator"></a>Controllo della visibilità di un'icona o di un elemento Decorator
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Un *elemento Decorator* è un'icona o una riga di testo visualizzata in una forma in un linguaggio specifico di dominio (DSL). È possibile far apparire l'elemento Decorator e scomparire a seconda dello stato delle proprietà nel modello. Ad esempio, in una forma che rappresenta una persona, è possibile che vengano visualizzate icone diverse in base al sesso, al numero di elementi figlio e così via.

## <a name="controlling-the-visibility-of-an-icon-or-decorator"></a>Controllo della visibilità di un'icona o di un elemento Decorator
 Nella procedura seguente si presuppone che sia già stata definita una forma e il relativo mapping a una classe di dominio. Per ulteriori informazioni, vedere [come definire un Domain-Specific Language](../modeling/how-to-define-a-domain-specific-language.md).

#### <a name="to-control-the-visibility-of-an-icon-or-text-decorator"></a>Per controllare la visibilità di un'icona o di un elemento Decorator del testo

1. Nel diagramma di definizione DSL aggiungere alla classe Shape le icone o gli elementi Decorator di testo che si desidera visualizzare.

   1. Fare clic con il pulsante destro del mouse sulla classe Shape, scegliere **Aggiungi**, quindi fare clic sul tipo di elemento Decorator obbligatorio.

   2. Imposta la proprietà **position** del Decorator. Più elementi Decorator possono avere la stessa posizione. Ad esempio, è possibile avere icone per i maschi e le femmine che condividono la stessa posizione.

   3. Imposta la proprietà **icona predefinita** di un elemento Decorator icona.

2. Selezionare la mappa degli elementi del diagramma, ovvero la linea grigia tra la classe Shape e la classe di dominio nel diagramma di definizione DSL.

3. Nella scheda **Mapping elementi Decorator** della finestra Dettagli DSL selezionare un elemento Decorator. Ad esempio, MaleDecorator.

4. Controllare la casella del **filtro visibilità** .

5. Se la proprietà del dominio che deve controllare la visibilità si trova sulla classe di dominio immediate, lasciare vuoto il **percorso della proprietà filtro** .

    In caso contrario, fare clic sul menu a discesa e passare alla relazione o alla classe in cui si trova la proprietà.

   - Per evitare la segnalazione di errori, è consigliabile non spostarsi tra le relazioni contrassegnate con "*" nello strumento di navigazione.

6. Impostare la **proprietà Filter** su una proprietà di dominio. Ad esempio, Gender.

7. Nell'elenco **voci di visibilità** aggiungere i valori di questa proprietà di dominio per cui l'elemento Decorator deve essere visibile. Ad esempio, maschio.

8. Ripetere i passaggi per ogni icona.

9. **Trasforma tutti i modelli**, compila ed Esegui e Apri un diagramma di test.

10. Quando si modifica il valore della proprietà di controllo, gli elementi Decorator dovrebbero apparire e scomparire.

    Spesso si desidera che la visibilità venga controllata da una formula più complessa rispetto a un semplice set di valori. Ad esempio, per fare in modo che un'icona dipenda dal numero di collegamenti di un determinato tipo o da fare in modo che dipenda da un valore che corrisponde a un determinato intervallo. In tal caso, utilizzare la procedura riportata di seguito.

#### <a name="to-control-the-visibility-of-a-decorator-based-on-a-formula"></a>Per controllare la visibilità di un elemento Decorator in base a una formula

1. Aggiungere una proprietà di dominio calcolato alla classe di dominio. Nella finestra **Proprietà** impostare i valori seguenti:

     **Navigable =** `False` **: nasconde la proprietà dall'utente**

     **Kind =** `Calculated` **: indica che verrà fornito codice per il calcolo del valore**

     **Nome** , ad esempio **DecoratorControl**

     **Digitare**  =  `Boolean`

     Per altre informazioni, vedere [proprietà di archiviazione calcolate e personalizzate](../modeling/calculated-and-custom-storage-properties.md).

2. Rendere la nuova proprietà controllare la visibilità dell'elemento Decorator.

    1. Selezionare la mappa degli elementi del diagramma, ovvero la linea grigia dalla classe di dominio alla forma. Nella finestra **Dettagli DSL** aprire la scheda **DecoratorMap** .

    2. Controllare la casella del **filtro visibilità** .

    3. In **Proprietà filtro**selezionare la proprietà del controllo **DecoratorControl**.

    4. In **voci di visibilità**immettere `True`.

3. Fare clic su **trasforma tutti i modelli** nella barra degli strumenti Esplora soluzioni.

4. Scegliere **Compila soluzione** dal menu **Compila** .

5. Fare doppio clic sul report di errore visualizzato: "*ClasseUtente* non contiene una definizione per GetDecoratorControlValue...".

     Viene aperto l'editor di testo in Dsl\GeneratedCode\DomainClasses.cs. Sopra l'errore evidenziato è presente un commento che richiede di aggiungere un metodo.

6. Si noti lo spazio dei nomi, la classe e il metodo mancanti.  Ad esempio, Company. FamilyTree. Person. GetDecoratorControlValue ().

7. In un file di codice separato scrivere una definizione di classe parziale che contiene il metodo mancante. Esempio:

    ```
    namespace Company.FamilyTree
    { partial class Person
      { bool GetDecoratorControlValue()
        {
          return this.Children.Count > 0;
    } } }
    ```

     Per ulteriori informazioni sulla personalizzazione del modello con il codice programma, vedere [esplorazione e aggiornamento di un modello nel codice programma](../modeling/navigating-and-updating-a-model-in-program-code.md).

8. Ricompilare ed eseguire la soluzione.

## <a name="see-also"></a>Vedere anche
 [Definizione di forme e connettori](../modeling/defining-shapes-and-connectors.md) [impostazione di un'immagine di sfondo in un diagramma](../modeling/setting-a-background-image-on-a-diagram.md) [esplorazione e aggiornamento di un modello nel codice programma](../modeling/navigating-and-updating-a-model-in-program-code.md) [scrittura di codice per personalizzare un Domain-Specific Language](../modeling/writing-code-to-customise-a-domain-specific-language.md)

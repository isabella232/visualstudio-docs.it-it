---
title: 'Diagrammi classi UML: linee guida | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
f1_keywords:
- vs.teamarch.logicalclassdiagram.overrideoperationsdialog
helpviewer_keywords:
- UML diagrams, class
- diagrams - modeling, class
- UML, class diagrams
- class diagrams - UML
- diagrams - modeling, UML class
ms.assetid: 94dbfd55-b300-4b49-9049-0831ed849486
caps.latest.revision: 56
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 804678985ae30d833b57fe7589f0903cf1edb291
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72652269"
---
# <a name="uml-class-diagrams-guidelines"></a>Diagrammi classi UML: linee guida
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In Visual Studio è possibile usare un *diagramma classi UML* per descrivere i tipi di dati e le relative relazioni separatamente rispetto all'implementazione. Il diagramma viene usato per concentrarsi sugli aspetti logici delle classi, anziché sull'implementazione.

 Per creare un diagramma classi UML, scegliere **nuovo diagramma livello o diagramma UML**dal menu **architettura** .

 Per individuare le versioni di Visual Studio che supportano questa funzionalità, vedere [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

> [!NOTE]
> In questo argomento vengono illustrati i diagrammi classi UML. Esiste un altro tipo di diagramma classi, che è possibile creare e usare per visualizzare il codice programma. Vedere [progettazione e visualizzazione di classi e tipi](http://go.microsoft.com/fwlink/?LinkId=142231).

## <a name="Using"></a>Uso di diagrammi classi UML
 È possibile usare un diagramma classi UML per vari scopi:

- Per fornire una descrizione indipendente dall'implementazione dei tipi usati in un sistema e passati tra i componenti.

     Ad esempio, il tipo Ordinazione pasto potrebbe essere implementato nel codice .NET a livello aziendale, in XML in corrispondenza delle interfacce tra componenti, in SQL nel database e in HTML nell'interfaccia utente. Nonostante tali implementazioni siano diverse nei dettagli, la relazione tra un tipo Ordinazione pasto e altri tipi, ad esempio Menu e Pagamento, è sempre la stessa. Il diagramma classi UML consente di illustrare tali relazioni separatamente dalle implementazioni.

- Per chiarire il glossario di termini usati per la comunicazione tra l'applicazione e gli utenti e nelle descrizioni delle esigenze degli utenti. Vedere [modellare i requisiti utente](../modeling/model-user-requirements.md).

     Si considerino ad esempio le descrizioni di storie utente, di casi di utilizzo o di altri requisiti di un'applicazione ristorante. In tali descrizioni vengono usati termini come Menu, Ordine, Pasto, Prezzo, Pagamento e così via. È possibile creare un diagramma classi UML che definisca le relazioni tra questi termini riducendo in questo modo il rischio di incoerenze nelle descrizioni dei requisiti nonché nell'interfaccia utente e nei documenti della guida.

### <a name="relationship-to-other-diagrams"></a>Relazione con altri diagrammi
 Un diagramma classi UML viene in genere creato con altri diagrammi di modellazione per fornire descrizioni dei tipi usati. In ogni caso, la rappresentazione fisica dei tipi non è implicita nei diagrammi.

 Diagramma di attività

 Tipo di dati che passano attraverso un nodo oggetto.

 Tipi di pin di input e output e di nodi parametro attività.

 Vedere [diagrammi di attività UML: linee guida](../modeling/uml-activity-diagrams-guidelines.md).

 Diagramma sequenza

 Tipi di parametri e di valori restituiti di messaggi.

 Tipi di linee di vita. La classe di una linea di vita deve includere le operazioni per tutti i messaggi che può ricevere.

 Vedere [diagrammi di sequenza UML: linee guida](../modeling/uml-sequence-diagrams-guidelines.md).

 Diagramma dei componenti

 Interfacce di componenti con le relative operazioni.

 Vedere [diagrammi di componenti UML: linee guida](../modeling/uml-component-diagrams-guidelines.md).

 Diagramma caso di utilizzo

 Tipi indicati nelle descrizioni degli obiettivi e dei passaggi di un caso d'uso.

 Vedere [diagrammi caso di utilizzo UML: linee guida](../modeling/uml-use-case-diagrams-guidelines.md).

## <a name="BasicSteps"></a>Passaggi di base per la creazione di diagrammi classi
 Per informazioni di riferimento sugli elementi nei diagrammi classi UML, vedere [diagrammi classi UML:](../modeling/uml-class-diagrams-reference.md)informazioni di riferimento.

> [!NOTE]
> I passaggi dettagliati per la creazione di uno dei diagrammi di modellazione sono descritti in [modificare modelli e diagrammi UML](../modeling/edit-uml-models-and-diagrams.md).

#### <a name="to-create-a-uml-class-diagram"></a>Per creare un diagramma classi UML

1. Scegliere **nuovo diagramma livello o UML**dal menu **architettura** .

2. In **modelli**scegliere **diagramma classi UML**.

3. Assegnare un nome al diagramma.

4. In **Aggiungi a progetto di modello**selezionare un progetto di modello esistente nella soluzione oppure **creare un nuovo progetto di modello**, quindi scegliere **OK**.

     Viene visualizzato un nuovo diagramma classi con la casella degli strumenti **diagramma UMLClass** . La casella degli strumenti contiene le relazioni e gli elementi necessari.

#### <a name="to-draw-a-uml-class-diagram"></a>Per creare un tipo di diagramma classi UML

1. Per creare un tipo, scegliere lo strumento **classe**, **interfaccia** o **enumerazione** nella casella degli strumenti, quindi fare clic su una parte vuota del diagramma. Se non è possibile visualizzare la casella degli strumenti, premere CTRL+ALT+X.

2. Per aggiungere attributi o operazioni ai tipi o a valori letterali a un'enumerazione, scegliere l'intestazione **attributi**, **operazioni** o **valori letterali** nel tipo e premere INVIO.

     È possibile scrivere una firma, ad esempio `f(x:Boolean):Integer`. Vedere [attributi e operazioni](#AttributesAndOperations).

     Per aggiungere rapidamente diversi elementi, premere INVIO due volte alla fine di ogni elemento. È possibile usare i tasti di direzione per spostarsi verso l'alto e verso il basso nell'elenco.

3. Per espandere o comprimere un tipo, scegliere l'icona con la freccia di espansione in alto a sinistra. È anche possibile espandere e comprimere la sezione **attributi** e **operazioni** di una classe o di un'interfaccia.

4. Per creare collegamenti di associazioni, ereditarietà o dipendenza tra i tipi, fare clic sullo strumento di relazione appropriato, quindi sul tipo di origine e infine sul tipo di destinazione.

5. Per creare i tipi in un pacchetto, creare un pacchetto utilizzando lo strumento **pacchetto** , quindi creare nuovi tipi e pacchetti all'interno del pacchetto. È anche possibile usare il comando copia per copiare i tipi e incollarli in un pacchetto.

6. Ogni diagramma è una visualizzazione in un modello condiviso tra altri diagrammi nello stesso progetto. Per visualizzare una visualizzazione albero del modello completo, scegliere **Visualizza**, **altre finestre**, **Esplora modelli UML**.

## <a name="UsingTypes"></a>Utilizzo di classi, interfacce ed enumerazioni
 Sono disponibili tre tipi standard di classificatore nella casella degli strumenti, Questi sono denominati *tipi* in tutto questo documento.

 ![Una classe, un'enumerazione e un'interfaccia](../modeling/media/uml-classguidetypes.png "UML_ClassGuideTypes")

- Utilizzare **le classi** (1) per rappresentare i dati o i tipi di oggetto per la maggior parte degli scopi.

- Usare le **interfacce** (2) in un contesto in cui è necessario distinguere tra le interfacce pure e le classi concrete con implementazioni interne. Questa differenza è utile quando lo scopo del diagramma è descrivere un'implementazione del software. È meno utile quando si modellano dati passivi o qualora si definiscano concetti usati per descrivere i requisiti utente.

- Utilizzare un' **enumerazione** (3) per rappresentare un tipo con un numero limitato di valori letterali, ad esempio `Stop` e `Go`.

  - Aggiungere i valori letterali all'enumerazione. Assegnare a ognuno un nome distinto.

  - Se si vuole, è anche possibile fornire un valore numerico per ogni valore letterale. Aprire il menu di scelta rapida per il valore letterale nell'enumerazione, scegliere **Proprietà**, quindi digitare un numero nel campo **valore** nella finestra **proprietà** .

  Assegnare a ogni tipo un nome univoco.

### <a name="getting-types-from-other-diagrams"></a>Recupero dei tipi da altri diagrammi
 È possibile visualizzare i tipi di un altro diagramma nel diagramma classi UML.

 Diagramma classi UML

 È possibile visualizzare una classe in più diagrammi classi UML. Quando è stata creata una classe in un diagramma, trascinare la classe da **Esplora modelli UML** nell'altro diagramma.

 Questa operazione è utile se si vuole che ogni diagramma si concentri su un gruppo di relazioni specifico.

 È possibile ad esempio mostrare le associazioni tra Ordinazione pasto e Menu ristorante in un diagramma e le associazioni tra Ordinazione pasto e Pagamento nell'altro diagramma.

 Diagramma dei componenti

 Se sono state definite interfacce nei componenti di un diagramma dei componenti, è possibile trascinare un'interfaccia da **Esplora modelli UML** nel diagramma classi. Nel diagramma classe è possibile definire i metodi inclusi nell'interfaccia.

 Vedere [diagrammi di componenti UML: linee guida](../modeling/uml-component-diagrams-guidelines.md).

 Diagramma di sequenza UML

 È possibile creare classi e interfacce dalle linee di vita in un diagramma di sequenza, quindi trascinare la classe da **Esplora modelli UML** in un diagramma classi UML. Ogni linea di vita in un diagramma di sequenza rappresenta un'istanza di un oggetto, un componente o un attore.

 Per creare una classe da una linea di vita, aprire il menu di scelta rapida per la linea di vita, quindi scegliere **Crea classe** o **Crea interfaccia**. Vedere [diagrammi di sequenza UML: linee guida](../modeling/uml-sequence-diagrams-guidelines.md).

## <a name="AttributesAndOperations"></a>Attributi e operazioni
 Un attributo (4) è un valore denominato che ogni istanza di un tipo può avere. L'accesso a un attributo non modifica lo stato dell'istanza.

 Un'operazione (5) è un metodo o una funzione che le istanze del tipo possono eseguire. Può restituire un valore. Se la proprietà di **query** è true, non è possibile modificare lo stato dell'istanza.

 Per aggiungere un attributo o un'operazione a un tipo, aprire il menu di scelta rapida per il tipo, scegliere **Aggiungi**, quindi scegliere **attributo** o **operazione**.

 Per visualizzarne le proprietà, aprire il menu di scelta rapida per l'attributo o l'operazione, quindi scegliere **Proprietà**. Le proprietà vengono visualizzate nella finestra **Proprietà** .

 Per visualizzare le proprietà dei parametri di un'operazione, scegliere <strong>[...]</strong> nella proprietà **Parameters** . Verrà visualizzata una nuova finestra di dialogo delle proprietà.

 Per informazioni dettagliate su tutte le proprietà da impostare, vedere:

- [Proprietà di attributi in diagrammi classi UML](../modeling/properties-of-attributes-on-uml-class-diagrams.md)

- [Proprietà di operazioni in diagrammi classi UML](../modeling/properties-of-operations-on-uml-class-diagrams.md)

### <a name="types-of-attributes-and-operations"></a>Tipi di attributi e di operazioni
 Ogni *tipo* di un attributo o di un'operazione e di ogni tipo di parametro può essere uno dei seguenti:

- **(nessuno)** : è possibile lasciare un tipo non specificato nella firma omettendo i due punti precedenti (`:`).

- Uno dei tipi primitivi standard: **Boolean**, **Integer**, **String**.

- Un tipo definito nel modello.

- Un valore con parametri di un tipo di modello, scritto modello \<Parameter >. Vedere [tipi di modello](#Templates).

  È anche possibile scrivere il nome di un tipo che non è stato ancora definito nel modello. Il nome verrà elencato in **tipi non specificati** in Esplora modelli UML.

> [!NOTE]
> Se successivamente si definisce una classe o un'interfaccia di quel nome nel modello, gli attributi e le operazioni meno recenti faranno ancora riferimento all'elemento in Tipi non specificati. Se si vuole fare in modo che facciano riferimento alla nuova classe, è necessario visitare ogni attributo o operazione e reimpostare il tipo, selezionando la nuova classe dal menu a discesa.

#### <a name="multiple-types"></a>Più tipi
 È possibile impostare una molteplicità di tipi di attributo, operazione o parametro.

 I valori consentiti sono:

 `[1]`

 Un valore del tipo specificato. Questa è l'impostazione predefinita.

 `[0..1]`

 **Null** o un valore del tipo specificato.

 `[*]`

 Una raccolta di un numero qualsiasi di istanze del tipo specificato.

 `[1..*]`

 Una raccolta di almeno un'istanza del tipo specificato.

 `[n..m]`

 Una raccolta di istanze tra `n` e `m` del tipo specificato.

 Se la molteplicità è maggiore di 1, è anche possibile impostare le proprietà seguenti:

- Istrued-se true, la raccolta ha **un ordine definito** .

- **Univoco** : Se true, non sono presenti valori duplicati nella raccolta.

### <a name="visibility"></a>Visibility
 *Visibility* indica se è possibile accedere all'attributo o all'operazione all'esterno della definizione della classe. I valori consentiti sono:

 **Public**

 **+**

 Accessibile da tutti gli altri tipi.

 **Private**

 **-**

 Accessibile solo alla definizione interna di questo tipo.

 **Pacchetto**

 **~**

 Accessibile solo all'interno del pacchetto che contiene questo tipo e in tutti i pacchetti che lo importano in modo esplicito. Vedere [definizione di spazi dei nomi e pacchetti](#Packages).

 **Protected**

 **#**

 Accessibile solo a questo tipo e ai tipi che ereditano da esso. Vedere [ereditarietà](#Inheritance).

### <a name="setting-the-signature-of-an-attribute-or-an-operation"></a>Impostazione della firma di un attributo o di un'operazione
 La firma di un attributo o di un'operazione è una raccolta di proprietà quali visibilità, nome, parametri (per le operazioni) e tipo.

 È possibile scrivere una firma direttamente nel diagramma. Fare clic sull'operazione o sull'attributo per selezionarlo, quindi farvi di nuovo clic.

 Scrivere la firma usando il formato seguente:

```
visibility attribute-name : Type
```

 \- oppure -

```
visibility operation-name (parameter1 : Type1, ...) : Type
```

 Esempio:

```
+ AddItem (item : MenuItem, quantity : Integer) : Boolean
```

 Usare la forma breve di visibilità. Il valore predefinito è `+` (pubblico).

 Ogni tipo può essere costituito da tipi definiti nel modello, da tipi standard come Numero intero o Stringa o dal nome di un nuovo tipo non ancora definito.

> [!NOTE]
> Se si scrive un nome senza un tipo in un elenco di parametri, esso indica il nome del parametro anziché il tipo. In questo esempio MenuItem e Integer diventano i nomi di due parametri con tipi non specificati:
>
> `AddItem(MenuItem, Integer) /* parameter names, not types! */`

 Per impostare la molteplicità di un tipo in una firma, scrivere la molteplicità in parentesi quadrate dopo il nome del tipo, ad esempio:

```
+ AddItems (items : MenuItem [1..*])
+ MenuContent : MenuItem [*]
```

 Se l'operazione o l'attributo è statico, il nome verrà visualizzato sottolineato nella firma. Se è astratto, il nome verrà visualizzato in corsivo.

 Tuttavia, è possibile impostare solo le proprietà **is static** e **is abstract** nella finestra **proprietà** .

#### <a name="full-signature"></a>Firma completa
 Quando si modifica la firma di un attributo o di un'operazione, alcune proprietà aggiuntive potrebbero venire visualizzate alla fine della riga e dopo ogni parametro. Vengono anche racchiuse tra parentesi graffe {...}. È possibile modificare o aggiungere tali proprietà. Esempio:

```
+ AddItems (items: MenuItem [1..*] {unique, ordered})
+ GetItems (filter: String) : MenuItem [*] {ordered, query}
```

 Di seguito sono riportate le proprietà:

 `unique`

 **Univoco**

 Non sono presenti valori duplicati nella raccolta. Si applica ai tipi con molteplicità maggiore di 1.

 `ordered`

 **Ordinato**

 La raccolta è una sequenza. Se false, non è stato definito il primo elemento. Si applica ai tipi con molteplicità maggiore di 1.

 `query`

 **Query**

 L'operazione non modifica lo stato dell'istanza. Si applica solo alle operazioni.

 `/`

 **Derivato**

 L'attributo viene calcolato dai valori degli altri attributi o associazioni.

 Prima del nome di un attributo viene visualizzato "/". Esempio:

```
/TotalPrice: Integer
```

 In genere, la firma completa viene visualizzata nel diagramma solo durante la modifica. Al termine della modifica, le proprietà aggiuntive vengono nascoste. Se si desidera visualizzare la firma completa sempre, aprire il menu di scelta rapida per il tipo, quindi scegliere **Mostra firma completa**.

## <a name="Associations"></a>Disegno e utilizzo di associazioni
 Usare un'associazione per rappresentare qualsiasi tipo di collegamento tra due elementi, indipendentemente dal modo in cui il collegamento viene implementato nel software. È possibile ad esempio usare un'associazione per rappresentare un puntatore in C#, una relazione in un database o un riferimento incrociato da una parte di un file XML all'altra. Può rappresentare un'associazione tra oggetti nel mondo reale, quali la terra e il sole. L'associazione non specifica il modo in cui il collegamento è rappresentato, ma solo che l'informazione esiste.

### <a name="properties-of-an-association"></a>Proprietà di un'associazione
 Dopo avere creato un'associazione, impostarne le proprietà. Aprire il menu di scelta rapida per l'associazione, quindi scegliere **Proprietà**.

 Oltre alle proprietà dell'associazione nel suo complesso, ogni *ruolo*, ovvero ogni estremità dell'associazione, dispone di alcune proprietà. Per visualizzarli, espandere il **primo ruolo** e il secondo proprietà del **ruolo** .

 Alcune proprietà di ogni ruolo sono visibili direttamente nel diagramma. Le visualizzazioni sono le seguenti:

- Role name. Viene visualizzato all'estremità appropriata dell'associazione nel diagramma. È possibile impostarlo nel diagramma o nella finestra **Proprietà** .

- **Molteplicità**, che per impostazione predefinita è **1**. Viene anche visualizzato nel diagramma accanto all'estremità appropriata dell'associazione.

- **Aggregazione**. Questo valore viene visualizzato come forma di rombo a un'estremità del connettore. È possibile usarlo per indicare che le istanze nel ruolo di aggregazione contengono le istanze dell'altro ruolo.

- **È esplorabile**. Se true per un solo ruolo, viene visualizzata una freccia nella direzione esplorabile. È possibile usare questo valore per indicare l'esplorabilità di collegamenti e relazioni del database nel software.

  Per informazioni dettagliate su queste e altre proprietà, vedere [proprietà delle associazioni nei diagrammi classi UML](../modeling/properties-of-associations-on-uml-class-diagrams.md).

### <a name="navigability"></a>Esplorabilità
 Quando si disegna un'associazione, viene visualizzata una freccia a un'estremità per indicare che è esplorabile in quella direzione. Ciò risulta utile se il diagramma classi rappresenta classi del software e le associazioni rappresentano puntatori o riferimenti. Quando tuttavia si usa il diagramma classi per rappresentare entità e relazioni o concetti aziendali, è meno importante rappresentare l'esplorabilità. In questo caso, è preferibile disegnare le associazioni senza frecce. Questa operazione può essere eseguita impostando la proprietà **is navigable** su entrambe le estremità dell'associazione su true. Per semplificare questa operazione, è possibile scaricare il codice di esempio di [modellazione del dominio UML](http://code.msdn.microsoft.com/UML-Domain-Modeling-6df6f7f4).

### <a name="attributes-and-associations"></a>Attributi e associazioni
 Un'associazione è la rappresentazione grafica di un attributo. Ad esempio, anziché creare una classe Ristorante con un attributo di tipo Menu, è possibile creare un'associazione da Ristorante a Menu.

 Ogni nome di attributo diventa il nome di un ruolo. Viene visualizzato all'estremità opposta dell'associazione del tipo proprietario. Osservare, ad esempio, `myMenu` nell'illustrazione.

 In genere, è consigliabile usare gli attributi solo per i tipi che non vengono inseriti nel diagramma, ad esempio i tipi primitivi.

 ![Associazione e attributi equivalenti](../modeling/media/uml-classguideattrib.png "UML_ClassGuideAttrib")

## <a name="Inheritance"></a> Ereditarietà
 Utilizzare lo strumento **ereditarietà** per creare le relazioni seguenti:

- Una relazione *generalizzazione* tra un tipo specializzato e un tipo generale

   \- oppure -

- Una relazione di *realizzazione* tra una classe e un'interfaccia implementata.

  Non è possibile creare cicli nelle relazioni di ereditarietà.

### <a name="generalization"></a>Generalizzazione
 Con Generalizzazione si intende che il tipo specializzato o derivato eredita attributi, operazioni e associazioni del tipo generale o di base.

 Il tipo generale viene visualizzato all'estremità della freccia della relazione.

 Le operazioni e gli attributi ereditati non vengono in genere mostrati nei tipi specializzati. È possibile però aggiungere le operazioni ereditate nell'elenco di operazioni del tipo specializzato. Ciò si rivela utile se si vuole eseguire l'override di alcune proprietà di un'operazione nel tipo specializzato o se si vuole indicare che il codice di implementazione deve eseguire tale operazione.

##### <a name="to-override-an-operations-definition-in-a-specializing-type"></a>Per eseguire l'override della definizione di un'operazione in un tipo specializzato

1. Fare clic sulla relazione generalizzazione.

    La relazione verrà visualizzata evidenziata con un tag azioni accanto.

2. Fare clic sul tag Action, quindi su **override Operations**.

    Verrà visualizzata la finestra di dialogo **operazioni di sostituzione** .

3. Selezionare le operazioni che si desidera visualizzare nel tipo specializzato, quindi fare clic su **OK**.

   Le operazioni selezionate verranno visualizzate nel tipo specializzato.

### <a name="realization"></a>Realizzazione
 Con Realizzazione si intende che una classe implementa gli attributi e le operazioni specificati dall'interfaccia. L'interfaccia si trova all'estremità della freccia del connettore.

 Quando si crea un connettore di realizzazione, le operazioni dell'interfaccia vengono replicate automaticamente nella classe di realizzazione. Se vengono aggiunte nuove operazioni a un'interfaccia, esse vengono replicate nelle relative classi di realizzazione.

 Dopo avere creato una relazione realizzazione, è possibile convertirla in notazione simbolo. Fare clic con il pulsante destro del mouse sulla relazione e scegliere **Mostra come simbolo**.

 In questo modo è possibile rappresentare le interfacce implementate da una classe senza ingombrare i diagrammi classi con collegamenti di realizzazione. È anche possibile mostrare le classi e l'interfaccia da esse implementata in diagrammi separati.

 ![Realizzazione mostrata con connettore e Lollipop](../modeling/media/uml-classguiderealize.png "UML_ClassGuideRealize")

## <a name="Templates"></a>Tipi di modello
 È possibile definire un tipo generico o di modello contenente parametri di altri tipi o valori.

 È possibile ad esempio creare un Dizionario generico contenente parametri dei tipi chiave e valore:

 ![Classe modello con due parametri](../modeling/media/uml-classguidetemplate1.png "UML_ClassGuideTemplate1")

#### <a name="to-create-a-template-type"></a>Per creare un tipo di modello

1. Creare una classe o un'interfaccia che diventerà il tipo di modello. Assegnargli un nome, ad esempio `Dictionary`.

2. Aprire il menu di scelta rapida per il nuovo tipo, quindi scegliere **Proprietà**.

3. Nella finestra **Proprietà** fare clic su **[...]** nel campo **parametri modello** .

    Verrà visualizzata la finestra di dialogo **Editor della raccolta di parametri del modello** .

4. Scegliere **Aggiungi**.

5. Impostare la proprietà nome sul nome di un parametro del tipo di modello, ad esempio `Key`.

6. Imposta il **tipo di parametro**. Il valore predefinito è **Class**.

7. Se si desidera che il parametro accetti solo le classi derivate di una particolare classe di base, impostare **valore vincolato** sulla classe di base desiderata.

8. Aggiungere tutti i parametri necessari, quindi scegliere **OK**.

9. Aggiungere gli attributi e le operazioni al tipo di modello come per le altre classi.

     È possibile utilizzare parametri il cui tipo è la **classe**, l' **interfaccia** o l' **enumerazione** nella definizione di attributi e operazioni. Usando ad esempio le classi di parametri `Key` e `Value`, è possibile definire in `Dictionary` l'operazione seguente:

     `Get(k : Key) : Value`

     È possibile usare un parametro il cui tipo è **Integer** come associato in una molteplicità. È possibile ad esempio usare il parametro numero intero max per definire la molteplicità di un attributo come `[0..max]`.

   Dopo avere creato i tipi di modello, è possibile usarli per definire le associazioni del modello:

   ![Classe associata dal modello di dizionario](../modeling/media/uml-classguidetemplate2.png "UML_ClassGuideTemplate2")

#### <a name="to-use-a-template-type"></a>Per usare un tipo di modello

1. Creare un nuovo tipo, ad esempio `AddressTable`.

2. Aprire il menu di scelta rapida per il nuovo tipo, quindi scegliere **Proprietà**.

3. Nella proprietà **associazione modello** selezionare il tipo di modello, ad esempio `Dictionary`, dall'elenco a discesa.

4. Espandere la proprietà di **associazione del modello** .

     Verrà visualizzata una riga per ogni parametro del tipo di modello.

5. Impostare ogni parametro su un valore appropriato. Impostare ad esempio il parametro `Key` su una classe denominata `Name`.

## <a name="Packages"></a>Pacchetti
 In un diagrammi classi UML è possibile visualizzare i pacchetti. Un pacchetto è un contenitore per altri elementi del modello. È possibile creare qualsiasi elemento in un pacchetto. Quando nel diagramma si sposta un pacchetto, si sposteranno anche gli elementi in esso contenuti.

 È possibile usare il controllo di compressione/espansione per nascondere o visualizzare il contenuto del pacchetto.

 Vedere [definire pacchetti e spazi dei nomi](../modeling/define-packages-and-namespaces.md).

## <a name="generating"></a>Generazione di codice da diagrammi classi UML
 Per avviare l'implementazione di classi in un diagramma classi UML, è possibile generare codice C# o personalizzare modelli per la generazione di codice. Per avviare la generazione di codice usando i modelli C# forniti:

- Aprire il menu di scelta rapida per il diagramma o un elemento, scegliere **genera codice**, quindi impostare le proprietà necessarie.

     Per altre informazioni su come impostare queste proprietà e personalizzare i modelli forniti, vedere [generare codice da diagrammi classi UML](../modeling/generate-code-from-uml-class-diagrams.md).

## <a name="see-also"></a>Vedere anche
 [Modificare modelli e](../modeling/edit-uml-models-and-diagrams.md) DIAGRAMmi UML diagrammi [classi UML:](../modeling/uml-class-diagrams-reference.md) [modello di riferimento requisiti utente modelli](../modeling/model-user-requirements.md) di [componente UML: riferimenti](../modeling/uml-component-diagrams-reference.md) [diagrammi di sequenza UML: riferimento](../modeling/uml-sequence-diagrams-reference.md) [diagrammi caso di utilizzo UML: riferimenti](../modeling/uml-use-case-diagrams-reference.md) [UML Diagrammi componente: riferimento](../modeling/uml-component-diagrams-reference.md)

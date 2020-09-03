---
title: Stereotipi standard per i modelli UML | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML, stereotypes
- UML diagrams, stereotypes
ms.assetid: 8a8c2321-1cae-4ba8-bb9e-23495c3404d8
caps.latest.revision: 22
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a16c68b3b14be57fb0a6a45c740e5420a82c2ddf
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "72661044"
---
# <a name="standard-stereotypes-for-uml-models"></a>Stereotipi standard per modelli UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

È possibile aggiungere stereotipi a elementi del modello UML per fornire altre informazioni a chi legge o al computer per l'elaborazione. Gli stereotipi vengono definiti nei profili e ogni profilo fornisce un set di stereotipi. Alcuni profili vengono forniti con Visual Studio. Si possono anche definire i propri profili che possono contenere stereotipi personalizzati. Per altre informazioni, vedere [definire un profilo per estendere UML](../modeling/define-a-profile-to-extend-uml.md).

 Per individuare le versioni di Visual Studio che supportano questa funzionalità, vedere [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

## <a name="the-standard-profiles"></a>Profili standard
 I seguenti profili sono disponibili in un'edizione supportata di Visual Studio subito dopo l'installazione.

|Profilo|Scopo|
|-------------|-------------|
|[Profilo standard UML L2](#L2)|Set standard di stereotipi che possono essere usati per aggiungere altre informazioni su un elemento o una relazione.|
|[Profilo standard UML L3](#L3)|Set standard di stereotipi che possono essere usati per aggiungere altre informazioni su un elemento o una relazione.|
|[Profilo C#](#NetProfile)|Se si vuole che una classe o un altro elemento in un modello UML rappresenti il codice programma, è possibile indicarlo applicando uno degli stereotipi del profilo C#.<br /><br /> Questi stereotipi inoltre aggiungono le proprietà agli elementi del modello.|

 Quando si crea un nuovo modello UML, i profili standard UML L2 e L3 vengono collegati al modello, a meno che non si rimuovano i collegamenti.

 Per usare gli stereotipi in uno di questi profili, prima è necessario collegare il profilo a un pacchetto o a un modello contenente gli elementi a cui applicarli.

#### <a name="to-link-a-profile-to-a-model-or-a-package"></a>Per collegare un profilo a un modello o a un pacchetto

1. Aprire **Esplora modelli UML**. Scegliere **finestre**dal menu **architettura** , quindi fare clic su **Esplora modelli UML**.

2. Individuare un pacchetto o un modello contenente tutti gli elementi a cui applicare gli stereotipi nel profilo.

3. Fare clic con il pulsante destro del mouse sul pacchetto o sul modello, quindi scegliere **Proprietà**.

4. Nella finestra **Proprietà** impostare la proprietà **profili** sui profili desiderati.

#### <a name="to-remove-the-link-between-a-profile-and-a-model-or-package"></a>Per rimuovere il collegamento tra un profilo e un modello o un pacchetto

1. In Esplora modelli UML fare clic con il pulsante destro del mouse sul modello o sul pacchetto, quindi scegliere **Proprietà**.

2. Nella Finestra Proprietà impostare la proprietà **profiles** su Empty.

    > [!NOTE]
    > È possibile scollegare un profilo solo se nessuno degli elementi nel modello o nel pacchetto usa gli stereotipi del profilo.

#### <a name="to-apply-a-stereotype-to-a-model-element"></a>Per applicare uno stereotipo a un elemento del modello

1. Fare clic con il pulsante destro del mouse sull'elemento del modello in un diagramma o in **Esplora modelli UML**e quindi scegliere **Proprietà**.

2. Fare clic sulla proprietà **stereotipi** e selezionare gli stereotipi che si desidera applicare.

     Gli stereotipi selezionati vengono visualizzati tra «frecce di espansione» nell'elemento del modello, per la maggior parte dei tipi di elemento.

    > [!NOTE]
    > Se non è possibile visualizzare la proprietà **stereotipi** o se lo stereotipo desiderato non viene visualizzato, verificare che l'elemento del modello si trovi all'interno di un pacchetto o di un modello a cui è stato collegato il profilo appropriato.

3. Alcuni stereotipi consentono di impostare i valori di altre proprietà per l'elemento del modello. Per visualizzare queste proprietà, espandere la proprietà **stereotipi** .

### <a name="uml-standard-profile-l2"></a><a name="L2"></a> Profilo standard UML L2
 I seguenti stereotipi possono essere usati per specializzare il significato degli elementi del modello UML, a meno che il collegamento al profilo non sia stato rimosso dal modello.

 Il significato esatto di questi stereotipi è determinato dalle convenzioni locali e dagli strumenti che potrebbero essere usati per elaborare il modello.

|Stereotipo|Si applica a|Significato|
|----------------|----------------|-------------|
|ausiliario|Classe|Classe che supporta un'altra classe, in genere implementando la logica aggiuntiva. L'altra classe potrebbe avere lo stereotipo «focus».|
|chiamare|Dipendenza|La classe client chiama le operazioni del fornitore.|
|create|Dipendenza|La classe client crea le istanze del fornitore.|
|create|Message|Il mittente crea il ricevitore.|
|create|Operazione|Questa operazione è un costruttore.|
|deriva|Dipendenza|L'elemento client viene calcolato completamente o parzialmente dal fornitore.|
|elimina|Operazione|L'operazione elimina l'istanza.|
|documento|Elemento|«file» che non è un'origine o un eseguibile.|
|Entità|Componente|Il componente rappresenta un concetto di business.|
|eseguibile|Elemento|«file» eseguibile.|
|file|Elemento|File fisico.|
|stato attivo|Classe|Classe che definisce la logica di business principale, supportata da diverse classi «auxiliary».|
|framework|Pacchetto|Questo pacchetto definisce uno schema progettuale riutilizzabile.|
|implementa|Componente|Implementazione di uno stereotipo «specification».|
|implementationClass|Classe|La classe descrive un'implementazione e ogni istanza di runtime dispone di una classe di implementazione fissa. Si differenzia da «type».|
|crea istanza|Dipendenza|Il client crea le istanze del fornitore.|
|library|Elemento|«file» di libreria.|
|metaclass|Classe|Anche le istanze di questa classe sono classi.|
|modelLibrary|Pacchetto|Contiene gli elementi del modello che devono essere riutilizzati dai pacchetti da importare. In genere è definito come parte di un profilo e importato automaticamente dall'applicazione del profilo.|
|processo|Componente|Componente basato sulle transazioni o che contiene un thread.|
|realizzazione|Classe, interfaccia, componente|Descrive un'implementazione.|
|rifinisci|Dipendenza|La classe, il componente o il pacchetto client offre più informazioni del fornitore sulla specifica o sulla progettazione.|
|responsabilità|Dipendenza|Il commento dal lato fornitore della dipendenza definisce le responsabilità della classe o del componente client.|
|script|Elemento|«file» interpretabile.|
|trasmissione|Dipendenza|L'operazione di origine invia il segnale di destinazione.|
|service|Componente|Componente senza stato.|
|source|Elemento|«file» compilabile.|
|specifica|Classe, interfaccia, componente|Definisce il comportamento di un componente o di un oggetto senza definire come funziona internamente.|
|sottosistema|Componente|Parte di un sistema di grandi dimensioni. Un sottosistema in un diagramma caso di utilizzo è un componente con lo stereotipo subsystem.|
|traccia|Dipendenza|L'elemento client fa parte della progettazione che realizza il fornitore. Le due estremità di questa dipendenza sono in genere in modelli diversi. Uno di questi modelli è una realizzazione dell'altro.|
|type|Classe|Specifica il comportamento di un oggetto senza indicare come viene implementato. Un oggetto è un membro di un tipo se è conforme alla specifica.|
|utility|Classe|Raccolta di funzioni statiche. La classe non dispone di istanze.|

### <a name="uml-standard-profile-l3"></a><a name="L3"></a> Profilo standard UML L3
 I seguenti stereotipi possono essere usati per specializzare il significato degli elementi del modello UML, a meno che il profilo non sia stato scollegato dal modello.

 Il significato esatto di questi stereotipi è determinato dalle convenzioni locali e dagli strumenti che potrebbero essere usati per elaborare il modello.

|Stereotipo|Si applica a|Descrizione|
|----------------|----------------|-----------------|
|buildComponent|Componente|Raccolta di elementi usati per definire una build.|
|metaModel|Modello|Definisce un linguaggio di modellazione, ad esempio una variante di UML, o un linguaggio specifico del dominio.|
|systemModel|Modello|Modello che è una raccolta di modelli che si applicano allo stesso sistema, ad esempio una specifica, una realizzazione e le relazioni di traccia reciproche.|

## <a name="c-profile"></a><a name="NetProfile"></a> Profilo C#
 Gli stereotipi definiti in questo profilo consentono di indicare che un elemento del modello verrà tradotto in codice programma. Ogni stereotipo definisce proprietà aggiuntive che è possibile impostare nell'elemento del modello.

 Per rendere disponibili questi stereotipi, collegare un modello o un pacchetto al profilo C#. È quindi possibile applicare gli stereotipi agli elementi del modello in tale modello o pacchetto.

 Gli stereotipi disponibili, gli elementi a cui si applicano e le altre proprietà rese disponibili sono riepilogati nella tabella seguente.

|Stereotipo|Si applica a|Proprietà|
|----------------|----------------|----------------|
|**Classe C#**|Classe UML<br /><br /> Componente|**Attributi CLR**<br /><br /> **Is Partial**<br /><br /> **Sealed**<br /><br /> **Is Static**<br /><br /> **Is Unsafe**<br /><br /> **Visibilità del pacchetto**|
|**Struct C#**|Classe UML<br /><br /> Componente|**Attributi CLR**<br /><br /> **Is Partial**<br /><br /> **Is Unsafe**<br /><br /> **Visibilità del pacchetto**|
|**Membri globali C#**|Classe UML<br /><br /> Componente|**Attributi CLR**|
|**Interfaccia C#**|Interfaccia UML|**Attributi CLR**<br /><br /> **Is Partial**<br /><br /> **Visibilità del pacchetto**|
|**C# enum**|Enumerazione UML|**ClrAttributes**<br /><br /> **Base Type**|
|**Spazio dei nomi C#**|Pacchetto UML|**Attributi CLR**<br /><br /> **Base Name**<br /><br /> **Using Namespaces**|

## <a name="see-also"></a>Vedere anche
 [Aggiungere stereotipi agli elementi del modello UML](../modeling/add-stereotypes-to-uml-model-elements.md) [personalizzare il modello con profili e stereotipi](../modeling/customize-your-model-with-profiles-and-stereotypes.md) [definire un profilo per estendere UML](../modeling/define-a-profile-to-extend-uml.md)

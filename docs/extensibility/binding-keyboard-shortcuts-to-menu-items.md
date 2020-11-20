---
title: Associazione dei tasti di scelta rapida alle voci di menu | Microsoft Docs
description: Informazioni su come eseguire il mapping di una scelta rapida da tastiera in Visual Studio a un pulsante personalizzato, una voce di menu o un comando della barra degli strumenti per l'editor predefinito o per un editor personalizzato.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- keyboard command
- keyboards
- command key
- keyboard shortcuts
- menu items
ms.assetid: 19f483b6-4d3e-424e-9d68-dc129c788e47
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 112089581965b96133f2160341a13efe23329934
ms.sourcegitcommit: 5027eb5c95e1d2da6d08d208fd6883819ef52d05
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/20/2020
ms.locfileid: "94974629"
---
# <a name="bind-keyboard-shortcuts-to-menu-items"></a>Associa scelte rapide da tastiera a voci di menu
Per associare un tasto di scelta rapida a un comando di menu personalizzato, è sufficiente aggiungere una voce al file con *estensione vsct* per il pacchetto. In questo argomento viene illustrato come eseguire il mapping di una scelta rapida da tastiera a un pulsante personalizzato, una voce di menu o un comando della barra degli strumenti e come applicare il mapping della tastiera nell'editor predefinito o come limitarlo a un editor personalizzato.

 Per assegnare tasti di scelta rapida alle voci di menu di Visual Studio esistenti, vedere [identificare e personalizzare i tasti di scelta rapida](../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md).

## <a name="choose-a-key-combination"></a>Scegliere una combinazione di tasti
 Molti tasti di scelta rapida sono già in uso in Visual Studio. Non è consigliabile assegnare lo stesso collegamento a più di un comando perché le associazioni duplicate sono difficili da rilevare e potrebbero anche causare risultati imprevedibili. Pertanto, è consigliabile verificare la disponibilità di un collegamento prima di assegnarlo.

### <a name="to-verify-the-availability-of-a-keyboard-shortcut"></a>Per verificare la disponibilità di un tasto di scelta rapida

1. Nella finestra **strumenti**  >  **Opzioni**  >  **ambiente** selezionare **tastiera**.

2. Assicurarsi che **Usa nuovo collegamento in** sia impostato su **globale**.

3. Nella casella **premere i tasti di scelta rapida** Digitare il tasto di scelta rapida che si desidera utilizzare.

    Se il tasto di scelta rapida è già usato in Visual Studio, il **collegamento attualmente usato da** box visualizzerà il comando attualmente chiamato dal collegamento.

4. Provare combinazioni diverse di chiavi finché non ne viene individuato uno non mappato.

   > [!NOTE]
   > Le scelte rapide da tastiera che usano **ALT** possono aprire un menu e non eseguire direttamente un comando. Pertanto, il **collegamento attualmente utilizzato da** box può essere vuoto quando si digita un tasto di scelta rapida che include **ALT**. È possibile verificare che il collegamento non apra un menu chiudendo la finestra di dialogo **Opzioni** e quindi premendo i tasti.

   Nella procedura seguente si presuppone che si disponga di un VSPackage esistente con un comando di menu. Per ottenere assistenza, vedere [creare un'estensione con un comando di menu](../extensibility/creating-an-extension-with-a-menu-command.md).

### <a name="to-assign-a-keyboard-shortcut-to-a-command"></a>Per assegnare un tasto di scelta rapida a un comando

1. Aprire il file con *estensione vsct* per il pacchetto.

2. Creare una `<KeyBindings>` sezione vuota dopo `<Commands>` se non è già presente.

   > [!WARNING]
   > Per ulteriori informazioni sui tasti di scelta, vedere la pagina relativa all' [associazione](../extensibility/keybinding-element.md)di tasti.

    Nella `<KeyBindings>` sezione creare una `<KeyBinding>` voce.

    Impostare gli `guid`  `id` attributi e su quelli del comando che si desidera richiamare.

    Impostare l' `mod1` attributo su **Control**, **ALT** o **Shift**.

    La sezione delle combinazioni di tasti dovrebbe avere un aspetto simile al seguente:

   ```xml
   <KeyBindings>
       <KeyBinding guid="<name of command set>" id="<name of command id>"
           editor="guidVSStd97" key1="1" mod1="CONTROL"/>
   </KeyBindings>

   ```

   Se il tasto di scelta rapida richiede più di due chiavi, impostare gli `mod2` `key2` attributi e.

   Nella maggior parte dei casi, lo **spostamento** non deve essere usato senza un secondo modificatore perché la pressione della maggior parte delle chiavi alfanumeriche consente di digitare una lettera maiuscola o un simbolo.

   I codici a chiave virtuale consentono di accedere a tasti speciali a cui non è associato alcun carattere, ad esempio i tasti funzione e il tasto **BACKSPACE** . Per ulteriori informazioni, vedere [codici chiave virtuale](/windows/desktop/inputdev/virtual-key-codes).

   Per rendere il comando disponibile nell'editor di Visual Studio, impostare l' `editor` attributo su `guidVSStd97` .

   Per rendere il comando disponibile solo in un editor personalizzato, impostare l' `editor` attributo sul nome dell'editor personalizzato generato dal [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] modello di pacchetto quando è stato creato il pacchetto VSPackage che include l'editor personalizzato. Per trovare il valore del nome, esaminare la `<Symbols>` sezione per un `<GuidSymbol>` nodo il cui `name` attributo termina con " `editorfactory` ." Si tratta del nome dell'editor personalizzato.

## <a name="example-1"></a>Esempio 1
 In questo esempio il tasto di scelta rapida **CTRL** + **ALT** + **C** viene associato a un comando denominato `cmdidMyCommand` in un pacchetto denominato `MyPackage` .

```
<CommandTable>
. . .
<Commands>
. . .
</Commands>
<KeyBindings>
  <KeyBinding guid="guidMyPackageCmdSet" id="cmdidMyCommand"
      key1="C" mod1="CONTROL" mod2="ALT" editor="guidVSStd97" />
</KeyBindings>
. . .
</CommandTable>
```

## <a name="example-2"></a>Esempio 2
 Questo esempio Mostra come associare il tasto di scelta rapida **CTRL** + **B** a un comando denominato `cmdidBold` in un progetto denominato `TestEditor` . Il comando è disponibile solo nell'editor personalizzato e non in altri editor.

```xml
<KeyBinding guid="guidVSStd97" id="cmdidBold" editor="guidTestEditorEditorFactory" key1="B" mod1="Control" />
```

## <a name="see-also"></a>Vedere anche
- [Estensione di menu e comandi](../extensibility/extending-menus-and-commands.md)

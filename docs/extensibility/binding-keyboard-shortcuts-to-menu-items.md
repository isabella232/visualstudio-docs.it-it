---
title: Associazione dei tasti di scelta rapida alle voci di menu Documenti Microsoft
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
ms.openlocfilehash: 94feafbc614be61aaa4eef9e26669c0fbe901ed5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740030"
---
# <a name="bind-keyboard-shortcuts-to-menu-items"></a>Associare i tasti di scelta rapida alle voci di menu
Per associare un tasto di scelta rapida a un comando di menu personalizzato, è sufficiente aggiungere una voce al file *vsct* per il pacchetto. In questo argomento viene illustrato come eseguire il mapping di un tasto di scelta rapida a un pulsante personalizzato, una voce di menu o un comando della barra degli strumenti e come applicare il mapping della tastiera nell'editor predefinito o limitarlo a un editor personalizzato.

 Per assegnare tasti di scelta rapida alle voci di menu di Visual Studio esistenti, consultate Identificare e personalizzare i tasti di [scelta rapida.](../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md)

## <a name="choose-a-key-combination"></a>Scegliere una combinazione di tasti
 Molti tasti di scelta rapida sono già utilizzati in Visual Studio.Many keyboard shortcuts are already used in Visual Studio. È consigliabile non assegnare lo stesso collegamento a più di un comando perché le associazioni duplicate sono difficili da rilevare e possono anche causare risultati imprevisti. Pertanto, è consigliabile verificare la disponibilità di un collegamento prima di assegnarlo.

### <a name="to-verify-the-availability-of-a-keyboard-shortcut"></a>Per verificare la disponibilità di una scelta rapida da tastiera

1. Nella finestra**Ambiente** **opzioni** >  **strumenti,** > selezionare **Tastiera**.

2. Assicurarsi che **Usa nuovo collegamento in** sia impostato su **Globale**.

3. Nella casella **Premere i tasti di scelta rapida** digitare la scelta rapida da tastiera che si desidera utilizzare.

    Se il collegamento è già utilizzato in Visual Studio, il **collegamento attualmente utilizzato da** casella verrà visualizzato il comando che il collegamento chiama attualmente.

4. Provare diverse combinazioni di tasti fino a trovare uno che non è mappato.

   > [!NOTE]
   > Le scelte rapide da tastiera che utilizzano **Alt** possono aprire un menu e non eseguire direttamente un comando. Pertanto, la casella **Scelta rapida attualmente utilizzata da** potrebbe essere vuota quando si digita un collegamento che include **Alt**. È possibile verificare che il collegamento non apra un menu chiudendo la finestra di dialogo **Opzioni** e quindi premendo i tasti.

   La procedura seguente presuppone che si dispone di un VSPackage esistente con un comando di menu. Se hai bisogno di aiuto per farlo, dai un'occhiata a [Creare un'estensione con un comando](../extensibility/creating-an-extension-with-a-menu-command.md)di menu .

### <a name="to-assign-a-keyboard-shortcut-to-a-command"></a>Per assegnare una scelta rapida da tastiera a un comando

1. Aprire il file *vsct* per il pacchetto.

2. Creare una `<KeyBindings>` sezione `<Commands>` vuota dopo la se non è già presente.

   > [!WARNING]
   > Per ulteriori informazioni sulle associazioni di tasti, vedere [Associazione di](../extensibility/keybinding-element.md)tasti .

    Nella `<KeyBindings>` sezione, creare `<KeyBinding>` una voce.

    Impostare `guid` `id` gli attributi e su quelli del comando che si desidera richiamare.

    Impostare `mod1` l'attributo **su Control**, **Alt**o **Shift**.

    La sezione KeyBindings dovrebbe essere simile alla seguente:The KeyBindings section should look something like this:

   ```xml
   <KeyBindings>
       <KeyBinding guid="<name of command set>" id="<name of command id>"
           editor="guidVSStd97" key1="1" mod1="CONTROL"/>
   </KeyBindings>

   ```

   Se la scelta rapida da tastiera `mod2` richiede `key2` più di due tasti, impostare gli attributi e .

   Nella maggior parte dei casi, **Shift** non deve essere utilizzato senza un secondo modificatore perché premendolo già la maggior parte dei tasti alfanumerici digita una lettera maiuscola o un simbolo.

   I codici tasto virtuale consentono di accedere a tasti speciali a cui non è associato un carattere, ad esempio i tasti funzione e il tasto **BACKSPACE.** Per ulteriori informazioni, vedere [Codici tasto virtuale](/windows/desktop/inputdev/virtual-key-codes).

   Per rendere il comando disponibile nell'editor `editor` di `guidVSStd97`Visual Studio, impostare l'attributo su .

   Per rendere il comando disponibile solo in `editor` un editor personalizzato, impostare l'attributo sul nome dell'editor personalizzato generato dal modello di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] pacchetto quando è stato creato il pacchetto VSPackage che include l'editor personalizzato. Per trovare il valore del `<Symbols>` nome, `<GuidSymbol>` cercare `name` un nodo`editorfactory`il cui attributo termina con " ." Questo è il nome dell'editor personalizzato.

## <a name="example"></a>Esempio
 In questo esempio la scelta rapida da tastiera **Ctrl**+ `MyPackage`**Alt**+**C** viene associata a un comando denominato `cmdidMyCommand` in un pacchetto denominato .

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

## <a name="example"></a>Esempio
 In questo esempio la scelta rapida da `cmdidBold` tastiera **Ctrl**+**B** viene associata a un comando denominato in un progetto denominato `TestEditor`. Il comando è disponibile solo nell'editor personalizzato e non in altri editor.

```xml
<KeyBinding guid="guidVSStd97" id="cmdidBold" editor="guidTestEditorEditorFactory" key1="B" mod1="Control" />
```

## <a name="see-also"></a>Vedere anche
- [Estensione di menu e comandi](../extensibility/extending-menus-and-commands.md)

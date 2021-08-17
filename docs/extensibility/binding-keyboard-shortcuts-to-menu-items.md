---
title: Associazione dei tasti di scelta rapida alle voci di menu | Microsoft Docs
description: Informazioni su come eseguire il mapping di un tasto di scelta rapida in Visual Studio a un pulsante personalizzato, una voce di menu o un comando della barra degli strumenti per l'editor predefinito o un editor personalizzato.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- keyboard command
- keyboards
- command key
- keyboard shortcuts
- menu items
ms.assetid: 19f483b6-4d3e-424e-9d68-dc129c788e47
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: f9859ee7b280b6861dc7894f1768c0b83261ea23
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122058149"
---
# <a name="bind-keyboard-shortcuts-to-menu-items"></a>Associare i tasti di scelta rapida alle voci di menu
Per associare un tasto di scelta rapida a un comando di menu personalizzato, è sufficiente aggiungere una voce al file *vsct* per il pacchetto. Questo argomento illustra come eseguire il mapping di un tasto di scelta rapida a un pulsante personalizzato, una voce di menu o un comando della barra degli strumenti e come applicare il mapping della tastiera nell'editor predefinito o limitarlo a un editor personalizzato.

 Per assegnare tasti di scelta rapida Visual Studio voci di menu esistenti, vedere [Identificare e personalizzare i tasti di scelta rapida.](../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md)

## <a name="choose-a-key-combination"></a>Scegliere una combinazione di tasti
 Molti tasti di scelta rapida sono già usati in Visual Studio. Non è consigliabile assegnare lo stesso collegamento a più comandi perché le associazioni duplicate sono difficili da rilevare e possono anche causare risultati imprevedibili. È quindi buona idea verificare la disponibilità di un collegamento prima di assegnarlo.

### <a name="to-verify-the-availability-of-a-keyboard-shortcut"></a>Per verificare la disponibilità di un tasto di scelta rapida

1. Nella finestra **Tools**  >  **Options**  >  **Environment (Ambiente opzioni** strumenti) selezionare Keyboard **(Tastiera).**

2. Assicurarsi che **l'opzione Usa nuovo collegamento in** sia impostata su **Globale.**

3. Nella casella **Premere i tasti di scelta** rapida digitare il tasto di scelta rapida che si vuole usare.

    Se il collegamento è già usato  in Visual Studio, nella casella Collegamento attualmente usato da verrà visualizzato il comando attualmente chiamato dal collegamento.

4. Provare diverse combinazioni di chiavi finché non ne viene trovato uno di cui non è stato eseguito il mapping.

   > [!NOTE]
   > I tasti di scelta rapida **che usano ALT** possono aprire un menu e non eseguire direttamente un comando. Di conseguenza, **la casella Collegamento attualmente** usato da potrebbe essere vuota quando si digita un collegamento che include **ALT**. È possibile verificare che il collegamento non a open un menu chiudendo la **finestra** di dialogo Opzioni e quindi premendo i tasti.

   La procedura seguente presuppone che si abbia un VSPackage esistente con un comando di menu. Per assistenza, vedere Creare [un'estensione con un comando di menu](../extensibility/creating-an-extension-with-a-menu-command.md).

### <a name="to-assign-a-keyboard-shortcut-to-a-command"></a>Per assegnare un tasto di scelta rapida a un comando

1. Aprire il file *vsct* per il pacchetto.

2. Creare una sezione `<KeyBindings>` vuota dopo se non è già `<Commands>` presente.

   > [!WARNING]
   > Per altre informazioni sulle associazioni di tasti, vedere [Keybinding](../extensibility/keybinding-element.md).

    Nella sezione `<KeyBindings>` creare una `<KeyBinding>` voce.

    Impostare gli `guid`  attributi e su quelli del comando da  `id` richiamare.

    Impostare `mod1` l'attributo **su Control**, **ALT** o **SHIFT**.

    La sezione KeyBindings dovrebbe essere simile alla seguente:

   ```xml
   <KeyBindings>
       <KeyBinding guid="<name of command set>" id="<name of command id>"
           editor="guidVSStd97" key1="1" mod1="CONTROL"/>
   </KeyBindings>

   ```

   Se il tasto di scelta rapida richiede più di due tasti, impostare gli `mod2` attributi e `key2` .

   Nella maggior parte dei casi, **MAIUSC** non deve essere usato senza un secondo modificatore perché premendolo la maggior parte dei tasti alfanumerici digita una lettera maiuscola o un simbolo.

   I codici di chiave virtuale consentono di accedere a chiavi speciali a cui non è associato un carattere, ad esempio i tasti funzione e **il tasto Backspace.** Per altre informazioni, vedere [Codici di chiave virtuale](/windows/desktop/inputdev/virtual-key-codes).

   Per rendere disponibile il comando nell'editor Visual Studio, impostare `editor` l'attributo su `guidVSStd97` .

   Per rendere il comando disponibile solo in un editor personalizzato, impostare l'attributo sul nome dell'editor personalizzato generato dal modello di pacchetto quando è stato creato il pacchetto VSPackage che include `editor` [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] l'editor personalizzato. Per trovare il valore del nome, cercare nella `<Symbols>` sezione un nodo il cui attributo termina con `<GuidSymbol>` `name` `editorfactory` "." Nome dell'editor personalizzato.

## <a name="example-1"></a>Esempio 1
 In questo esempio la combinazione di tasti **CTRL** ALT C viene +  +  associata a un comando `cmdidMyCommand` denominato in un pacchetto denominato `MyPackage` .

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
 In questo esempio la combinazione di tasti **CTRL** B viene +  associata a un comando denominato `cmdidBold` in un progetto denominato `TestEditor` . Il comando è disponibile solo nell'editor personalizzato e non in altri editor.

```xml
<KeyBinding guid="guidVSStd97" id="cmdidBold" editor="guidTestEditorEditorFactory" key1="B" mod1="Control" />
```

## <a name="see-also"></a>Vedi anche
- [Estensione di menu e comandi](../extensibility/extending-menus-and-commands.md)

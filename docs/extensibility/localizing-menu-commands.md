---
title: Localizzazione dei comandi di menu | Microsoft Docs
description: Informazioni su come fornire testo localizzato per i comandi di menu e barra degli strumenti creando file con estensione vsct localizzati e file resx localizzati per il pacchetto VSPackage.
ms.custom: SEO-VS-2020
ms.date: 10/08/2019
ms.topic: how-to
helpviewer_keywords:
- localize
- localization
- vsct
- menu commands
- localize visual studio
- localize vsct
ms.assetid: b04ee0f6-82ea-47e6-853a-72382267d6da
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 421072452214828560234aeb3a23128a38d0d515
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122152237"
---
# <a name="localize-menu-commands"></a>Comandi di menu Localizza

È possibile fornire testo localizzato per i comandi di menu e barra degli strumenti creando file con estensione *vsct* e *resx* localizzati per il pacchetto VSPackage e quindi aggiornando i file di progetto per incorporare le modifiche.

Per informazioni su come localizzare l'esperienza di installazione, vedere [Localizzare i pacchetti VSIX.](../extensibility/localizing-vsix-packages.md)

## <a name="localize-command-names"></a>Localizzare i nomi dei comandi

Nei pacchetti VSPackage i comandi di menu e i pulsanti della barra degli strumenti sono definiti nel file *con estensione vsct.*

1. In **Esplora soluzioni** modificare il nome del file con estensione *vsct* da *filename.vsct* a *filename.en-US.vsct*.

2. Creare una copia di *filename.en-US.vsct* per ogni lingua localizzata.

    Assegnare un nome a ogni nome *file di copia.{ Locale}.vsct*, dove *{Locale} è* un nome di impostazioni cultura specifico. Per un elenco dei valori dei nomi delle impostazioni cultura, vedere [ID delle impostazioni locali assegnati da Microsoft.](/windows/uwp/publish/supported-languages)

    Questi nomi *file. I file Locale.vsct* conterranno il testo del menu localizzato per il pacchetto.

3. Aprire ogni nome *file. File Locale.vsct* per localizzare il testo.

   1. Modificare i [valori dell'elemento ButtonText](../extensibility/buttontext-element.md) in base alla lingua specifica.

   2. Se si specificano icone localizzate, modificare i [valori bitmap](../extensibility/bitmap-element.md) in modo che puntino ai file di destinazione.

      L'esempio seguente mostra il testo di un pulsante in inglese e spagnolo per un comando per aprire una finestra degli strumenti Family Tree Explorer.

      [*FamilyTree.en-US.vsct*]

   ```xml
   <Button guid="guidLocalizedPackageCmdSet" id="cmdidFamilyTree" priority="0x0100" type="Button">
     <Parent guid="guidSHLMainMenu" id="IDG_VS_WNDO_OTRWNDWS1"/>
     <Icon guid="guidImages" id="bmpPic2" />
     <Strings>
       <CommandName>cmdidFamilyTree</CommandName>
       <ButtonText>Family Tree Explorer</ButtonText>
     </Strings>
   </Button>
   ```

    [*FamilyTree.es-ES.vsct*]

   ```xml
   <Button guid="guidLocalizedPackageCmdSet" id="cmdidFamilyTree" priority="0x0100" type="Button">
     <Parent guid="guidSHLMainMenu" id="IDG_VS_WNDO_OTRWNDWS1"/>
     <Icon guid="guidImages" id="bmpPic2" />
     <Strings>
       <CommandName>cmdidFamilyTree</CommandName>
       <ButtonText>Explorar el arbol genealogico</ButtonText>
     </Strings>
   </Button>
   ```

## <a name="localize-other-text-resources"></a>Localizzare altre risorse di testo

Le risorse di testo diverse da nomi di comando sono definite nei file di risorse *(con estensione resx).*

1. Rinominare *VSPackage.resx* in *VSPackage.en-US.resx*.

2. Creare una copia del file *VSPackage.en-US.resx* per ogni lingua localizzata.

     Assegnare a ogni copia *il nome VSPackage.{ Locale}.resx,* dove *{Locale} è* un nome di impostazioni cultura specifico.

3. Rinominare *Resources.resx* *in Resources.en-US.resx*.

4. Creare una copia del file *Resources.en-US.resx* per ogni lingua localizzata.

     Assegnare a ogni copia il *nome Resources.{ Locale}.resx,* dove *{Locale} è* un nome di impostazioni cultura specifico.

5. Aprire ogni file *con estensione resx* per modificare i valori stringa in base alla lingua e alle impostazioni cultura specifiche. Nell'esempio seguente viene illustrata la definizione di risorsa localizzata per la barra del titolo di una finestra degli strumenti.

     [*Resources.en-US.resx*]

    ```xml
    <data name="ToolWindowTitle" xml:space="preserve">
      <value>Family Tree Explorer</value>
    </data>
    ```

     [*Resources.es-ES.resx*]

    ```xml
    <data name="ToolWindowTitle" xml:space="preserve">
      <value>Explorador del arbol genealogico</value>
    </data>
    ```

## <a name="incorporate-localized-resources-into-the-project"></a>Incorporare le risorse localizzate nel progetto

È necessario modificare il file *assemblyinfo.cs* e il file di progetto per incorporare le risorse localizzate.

1. Dal **nodo Proprietà** in **Esplora soluzioni** aprire *assemblyinfo.cs* o *assemblyinfo.vb* nell'editor.

2. Aggiungere la voce seguente.

    ```csharp
    [assembly: NeutralResourcesLanguage("en-US", UltimateResourceFallbackLocation.Satellite)]
    ```

     In questo modo viene impostata l'inglese (Stati Uniti) come lingua predefinita.

3. Scaricare il progetto.

4. Aprire il file di progetto nell'editor.

5. Nell'elemento `Project` radice aggiungere un elemento con un elemento corrispondente al `PropertyGroup` `UICulture` linguaggio predefinito.

    ```xml
    <PropertyGroup>
      <UICulture>en-US</UICulture>
    </PropertyGroup>
    ```

     In questo modo viene impostata l'inglese (Stati Uniti) come impostazioni cultura dell'interfaccia utente predefinite per Windows Presentation Foundation (WPF).

6. Individuare `ItemGroup` l'elemento che contiene `EmbeddedResource` gli elementi .

7. `EmbeddedResource`Nell'elemento che chiama *VSPackage.en-US.resx* sostituire l'elemento con un elemento impostato su , come `ManifestResourceName` indicato di `LogicalName` `VSPackage.en-US.Resources` seguito:

    ```xml
    <EmbeddedResource Include="VSPackage.en-US.resx">
      <MergeWithCTO>true</MergeWithCTO>
      <LogicalName>VSPackage.en-US.Resources</LogicalName>
    </EmbeddedResource>
    ```

8. Per ogni lingua localizzata, copiare l'elemento  `EmbeddedResource` per e impostare `VsPackage.en-US` **l'attributo Include** e l'elemento **LogicalName** della copia sulle impostazioni locali di destinazione.

9. A ogni elemento `VSCTCompile` localizzato aggiungere un `ResourceName` elemento che punta a , come illustrato `Menus.ctmenu` nell'esempio seguente:

    ```xml
    <ItemGroup>
      <VSCTCompile Include="LocalizedPackage.es-ES.vsct">
        <ResourceName>Menus.ctmenu</ResourceName>
      </VSCTCompile>
    </ItemGroup>
    ```

10. Salvare il file di progetto e ricaricare il progetto.

11. Compilare il progetto.

     In questo modo vengono creati un assembly principale e assembly di risorse per ogni linguaggio. Per informazioni sulla localizzazione del processo di distribuzione, vedere [Localizzare i pacchetti VSIX](../extensibility/localizing-vsix-packages.md)

## <a name="see-also"></a>Vedi anche

- [Estendere menu e comandi](../extensibility/extending-menus-and-commands.md)
- [Globalizzare e localizzare le applicazioni](../ide/globalizing-and-localizing-applications.md)

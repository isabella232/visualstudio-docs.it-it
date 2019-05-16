---
title: Localizzazione di comandi di Menu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- localize
- localization
- vsct
- menu commands
- localize visual studio
- localize vsct
ms.assetid: b04ee0f6-82ea-47e6-853a-72382267d6da
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: c879072b55729e249b1aecd665d6f470f4138a75
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/15/2019
ms.locfileid: "65686128"
---
# <a name="localizing-menu-commands"></a>Localizzazione dei comandi di menu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

È possibile fornire il testo localizzato per menu e barra degli strumenti dei comandi di creazione di file con estensione vsct localizzato e localizzato file con estensione resx per il pacchetto VSPackage e quindi aggiornando i file di progetto incorporare le modifiche.  
  
 Per informazioni su come localizzare l'esperienza di installazione, vedere [localizzazione di pacchetti VSIX](../extensibility/localizing-vsix-packages.md).  
  
## <a name="localizing-command-names"></a>Localizzare i nomi dei comandi  
 Nei pacchetti VSPackage, i comandi di menu e pulsanti della barra degli strumenti sono definiti nel file con estensione vsct.  
  
1. Nelle **Esplora soluzioni**, modificare il nome del file con estensione vsct da *filename*vsct per *filename*. en-US.vsct.  
  
2. Creare una copia del *filename*. en-US.vsct per ogni lingua localizzata.  
  
    Nome di ogni copia *nomefile*. *Impostazioni internazionali*vsct, dove *delle impostazioni locali* è un nome di impostazioni cultura particolari. Per un elenco di valori di nome impostazioni cultura, vedere [Locale IDs Assigned by Microsoft](https://msdn.microsoft.com/library/windows/apps/jj657969.aspx).  
  
    Questi *nomefile*. *Impostazioni locali*i file con estensione vsct conterrà il testo del menu localizzato per il pacchetto.  
  
3. Aprire ognuno *nomefile*. *Impostazioni locali*file vsct per localizzare il testo.  
  
   1. Modificare il [ButtonText](../extensibility/buttontext-element.md) elemento i valori come appropriato per la lingua particolare.  
  
   2. Se si intende fornire le icone localizzate, modificare il [Bitmap](../extensibility/bitmap-element.md) valori in modo che punti ai file di destinazione.  
  
      L'esempio seguente illustra l'inglese e spagnolo testo del pulsante aprire una finestra degli strumenti dell'albero genealogico Esplora un comando.  
  
      [FamilyTree.en-US.vsct]  
  
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
  
    [FamilyTree.es-ES.vsct]  
  
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
  
## <a name="localizing-other-text-resources"></a>Localizzazione di altre risorse di testo  
 Le risorse di testo diverso da nomi di comando vengono definite nei file di risorse (resx).  
  
1. Rinominare VSPackage.resx VSPackage.en-us. resx.  
  
2. Creare una copia del file VSPackage.en-us. resx per ogni lingua localizzata.  
  
     Assegnare un nome ogni copia del pacchetto VSPackage. *Delle impostazioni locali*resx, dove *delle impostazioni locali* è un nome di impostazioni cultura particolari.  
  
3. Rinominare Resources in Resources. en-us. resx.  
  
4. Creare una copia del file resources. en-us. resx per ogni lingua localizzata.  
  
     Ogni copia le risorse il nome. *Delle impostazioni locali*resx, dove *delle impostazioni locali* è un nome di impostazioni cultura particolari.  
  
5. Aprire ogni file con estensione resx per modificare i valori stringa come appropriato per la lingua particolare. Nell'esempio seguente illustra la definizione di risorsa localizzata per la barra del titolo di una finestra degli strumenti.  
  
     [Resources.en-US.resx]  
  
    ```xml  
    <data name="ToolWindowTitle" xml:space="preserve">  
      <value>Family Tree Explorer</value>  
    </data>  
    ```  
  
     [Resources.es-ES.resx]  
  
    ```xml  
    <data name="ToolWindowTitle" xml:space="preserve">  
      <value>Explorador del arbol genealogico</value>  
    </data>  
  
    ```  
  
## <a name="incorporating-localized-resources-into-the-project"></a>Incorporare le risorse localizzate nel progetto  
 È necessario modificare il file assemblyinfo.cs e il file di progetto per incorporare le risorse localizzate.  
  
1. Dal **delle proprietà** nodo nel **Esplora soluzioni**, aprire file assemblyinfo.cs o AssemblyInfo. vb nell'editor.  
  
2. Aggiungere la voce seguente.  
  
    ```csharp  
    [assembly: NeutralResourcesLanguage("en-US", UltimateResourceFallbackLocation.Satellite)]  
    ```  
  
     Consente di impostare inglese come lingua predefinita.  
  
3. Scaricare il progetto.  
  
4. Aprire il file di progetto nell'editor.  
  
5. Individuare il `ItemGroup` elemento contenente `EmbeddedResource` elementi.  
  
6. Nel `EmbeddedResource` elemento che chiama VSPackage.en-us. resx, sostituire il `ManifestResourceName` elemento con un `LogicalName` elemento, impostato su `VSPackage.en-US.Resources`, come indicato di seguito.  
  
    ```xml  
    <EmbeddedResource Include="VSPackage.en-US.resx">  
      <MergeWithCTO>true</MergeWithCTO>  
      <LogicalName>VSPackage.en-US.Resources</LogicalName>  
    </EmbeddedResource>  
    ```  
  
7. Per ogni lingua localizzata, copiare il `EmbeddedResource` elemento per VsPackage.en-US, quindi impostare il **inclusione** attributo e **LogicalName** elemento della copia in impostazioni locali di destinazione, come illustrato di seguito esempio.  
  
8. A ogni localizzato `VSCTCompile` elemento, aggiungere un' `ResourceName` elemento al quale punta `Menus.ctmenu`, come illustrato nell'esempio seguente.  
  
    ```xml  
    <ItemGroup>  
      <VSCTCompile Include="LocalizedPackage.es-ES.vsct">  
        <ResourceName>Menus.ctmenu</ResourceName>  
      </VSCTCompile>  
    </ItemGroup>  
    ```  
  
9. Salvare il file di progetto e ricaricare il progetto.  
  
10. Compilare il progetto.  
  
     Verrà creato un assembly principale e gli assembly di risorse per ogni lingua. Per informazioni sulla localizzazione il processo di distribuzione, vedere [localizzazione di pacchetti VSIX](../extensibility/localizing-vsix-packages.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Estensione di menu e comandi](../extensibility/extending-menus-and-commands.md)   
 [Confronto tra oggetti MenuCommand e OleMenuCommands](../misc/menucommands-vs-olemenucommands.md)   
 [Globalizzazione e localizzazione](https://msdn.microsoft.com/library/9a59696b-d89b-45bd-946d-c75da4732d02)

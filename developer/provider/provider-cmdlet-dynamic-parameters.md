---
title: Parametry dynamiczne polecenia cmdlet dostawcy | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8f1069f7-8fa8-4622-9e2c-af29b0b961c2
caps.latest.revision: 6
ms.openlocfilehash: 803fe4ae24a4f8022639c5b6d6298100859177ce
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56848461"
---
# <a name="provider-cmdlet-dynamic-parameters"></a>Parametry dynamiczne poleceń cmdlet dostawców

Dostawców można zdefiniować parametry dynamiczne, które są dodawane do polecenia cmdlet dostawcy, gdy użytkownik określi określoną wartość dla jednego statycznego parametrów polecenia cmdlet. Na przykład dodać dostawcę różnych parametrów dynamicznych na podstawie ścieżki, jakie użytkownik określi, gdy wywołana `Get-Item` lub `Set-Item` polecenia cmdlet dostawcy.

## <a name="dynamic-parameter-methods"></a>Metody parametr dynamiczny

Parametry dynamiczne są definiowane przez zaimplementowanie jednego z parametrów dynamicznych metod, takich jak [System.Management.Automation.Provider.Itemcmdletprovider.Getitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItemDynamicParameters) i [ System.Management.Automation.Provider.Itemcmdletprovider.Setitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItemDynamicParameters)metody s. Te metody zwracają obiekt, który ma właściwości publiczne, które są oznaczone za pomocą atrybutów podobne do występujących dla autonomicznych poleceń cmdlet. Poniżej przedstawiono przykład implementacji [System.Management.Automation.Provider.Itemcmdletprovider.Getitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItemDynamicParameters) metoda pobranych z dostawcą certyfikatów:

```csharp
protected override object GetItemDynamicParameters(string path)
{
    return new CertificateProviderDynamicParameters();
}
```

W przeciwieństwie do statycznych parametrów polecenia cmdlet dostawcy można określić właściwości tych parametrów w taki sam sposób, czy parametry są definiowane w autonomicznych poleceń cmdlet. Oto przykład klasy parametrów dynamicznych z dostawcą certyfikatów:

```csharp
internal sealed class CertificateProviderDynamicParameters
{
  /// <summary>
  /// Dynamic parameter the controls whether we only return
  /// code signing certs.
  /// </summary>
  [Parameter()]
  public SwitchParameter CodeSigningCert
  {
    get
    {
      {
        return codeSigningCert;
      }
    }

    set
    {
      {
        codeSigningCert = value;
      }
    }
  }

    private SwitchParameter codeSigningCert = new SwitchParameter();
}
```

## <a name="dynamic-parameters"></a>Parametry dynamiczne

Oto lista parametry statyczne, które mogą służyć do dodawania parametrów dynamicznych.

`Clear-Content` polecenia cmdlet można zdefiniować parametry dynamiczne, które są uruchamiane w `Path` parametru polecenia cmdlet Clear-wyczyść implementując [System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontentdynamicparameters* ](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContentDynamicParameters) metody.

`Clear-Item` polecenia cmdlet można zdefiniować parametry dynamiczne, które są uruchamiane w `Path` parametru `Clear-Item` polecenia cmdlet, implementując [System.Management.Automation.Provider.Itemcmdletprovider.Clearitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItemDynamicParameters) metody.

`Clear-ItemProperty` polecenia cmdlet można zdefiniować parametry dynamiczne, które są uruchamiane w `Path` parametru `Clear-ItemProperty` polecenia cmdlet, implementując [ System.Management.Automation.Provider.Ipropertycmdletprovider.Clearpropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearPropertyDynamicParameters) metody.

`Copy-Item` polecenia cmdlet można zdefiniować parametry dynamiczne, które są uruchamiane w `Path`, `Destination`, i `Recurse` parametry `Copy-Item` polecenia cmdlet, implementując [ System.Management.Automation.Provider.Containercmdletprovider.Copyitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItemDynamicParameters) metody.

Polecenie cmdlet Get-ChildItems można zdefiniować parametry dynamiczne, które są uruchamiane w `Path` i `Recures` parametry `Get-ChildItem` polecenia cmdlet, implementując [ System.Management.Automation.Provider.Containercmdletprovider.Getchilditemsdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItemsDynamicParameters) i [System.Management.Automation.Provider.Containercmdletprovider.Getchildnamesdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNamesDynamicParameters) metody.

`Get-Content` polecenia cmdlet można zdefiniować parametry dynamiczne, które są uruchamiane w `Path` parametru `Get-Content` polecenia cmdlet, implementując [ System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreaderdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReaderDynamicParameters) metody.

`Get-Item` polecenia cmdlet można zdefiniować parametry dynamiczne, które są uruchamiane w `Path` parametru `Get-Item` polecenia cmdlet, implementując [System.Management.Automation.Provider.Itemcmdletprovider.Getitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItemDynamicParameters) metody.

`Get-ItemProperty` polecenia cmdlet można zdefiniować parametry dynamiczne, które są uruchamiane w `Path` i `Name` parametry `Get-ItemProperty` polecenia cmdlet, implementując [ System.Management.Automation.Provider.Ipropertycmdletprovider.Getpropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetPropertyDynamicParameters) metody.

`Invoke-Item` polecenia cmdlet można zdefiniować parametry dynamiczne, które są uruchamiane w `Path` parametru `Invoke-Item` polecenia cmdlet, implementując [ System.Management.Automation.Provider.Itemcmdletprovider.Invokedefaultactiondynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultActionDynamicParameters) metody.

`Move-Item` polecenia cmdlet można zdefiniować parametry dynamiczne, które są uruchamiane w `Path` i `Destination` parametry `Move-Item` polecenia cmdlet, implementując [ System.Management.Automation.Provider.Navigationcmdletprovider.Moveitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItemDynamicParameters) metody.

`New-Item` polecenia cmdlet można zdefiniować parametry dynamiczne, które są uruchamiane w `Path`, `ItemType`, i `Value` parametry `New-Item` polecenia cmdlet, implementując [ System.Management.Automation.Provider.Containercmdletprovider.Newitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItemDynamicParameters) metody.

`New-ItemProperty` polecenia cmdlet można zdefiniować parametry dynamiczne, które są uruchamiane w `Path`, `Name`, `PropertyType`, i `Value` parametry `New-ItemProperty` polecenia cmdlet, implementując [ System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Newpropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.NewPropertyDynamicParameters) metody.

`New-PSDrive` polecenia cmdlet można zdefiniować parametry dynamiczne, które są uruchamiane w [System.Management.Automation.Psdriveinfo](/dotnet/api/System.Management.Automation.PSDriveInfo) obiektu zwróconego przez `New-PSDrive` polecenia cmdlet, implementując [ System.Management.Automation.Provider.Drivecmdletprovider.Newdrivedynamicparameters*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDriveDynamicParameters) metody.

`Remove-Item` Można zdefiniować parametry dynamiczne, które są uruchamiane w `Path` i `Recurse` parametry `Remove-Item` polecenia cmdlet, implementując [ System.Management.Automation.Provider.Containercmdletprovider.Removeitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItemDynamicParameters) metody.

`Remove-ItemProperty` Można zdefiniować parametry dynamiczne, które są uruchamiane w `Path` i `Name` parametry `Remove-ItemProperty` polecenia cmdlet, implementując [ System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Removepropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RemovePropertyDynamicParameters) metody.

`Rename-Item` polecenia cmdlet można zdefiniować parametry dynamiczne, które są uruchamiane w `Path` i `NewName` parametry `Rename-Item` polecenia cmdlet, implementując [ System.Management.Automation.Provider.Containercmdletprovider.Renameitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItemDynamicParameters) metody.

`Rename-ItemProperty` Można zdefiniować parametry dynamiczne, które są uruchamiane w `Path`, `Name`, i `NewName` parametry `Rename-ItemProperty` polecenia cmdlet, implementując [ System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Renamepropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RenamePropertyDynamicParameters) metody.

`Set-Content` polecenia cmdlet można zdefiniować parametry dynamiczne, które są uruchamiane w `Path` parametru `Set-Content` polecenia cmdlet, implementując [ System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentwriterdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriterDynamicParameters) metody.

`Set-Item` polecenia cmdlet można zdefiniować parametry dynamiczne, które są uruchamiane w `Path` i `Value` parametry `Set-Item` polecenia cmdlet, implementując [ System.Management.Automation.Provider.Itemcmdletprovider.Setitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItemDynamicParameters) metody.

`Set-ItemProperty` polecenia cmdlet można zdefiniować parametry dynamiczne, które są uruchamiane w `Path` i `Value` parametry `Set-Item` polecenia cmdlet, implementując [ System.Management.Automation.Provider.Ipropertycmdletprovider.Setpropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetPropertyDynamicParameters) metody.

`Test-Path` polecenia cmdlet można zdefiniować parametry dynamiczne, które są uruchamiane w `Path` parametru `Test-Path` polecenia cmdlet, implementując [ System.Management.Automation.Provider.Itemcmdletprovider.Invokedefaultactiondynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultActionDynamicParameters) metody.

## <a name="see-also"></a>Zobacz też

[Pisanie dostawcy programu PowerShell Windows](./writing-a-windows-powershell-provider.md)
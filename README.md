# WindowsPrivileges.pp

## Author

Bill Stewart (bstewart AT iname.com)

## License

**WindowsPrivileges.pp** is covered by the GNU Lesser Public License (LPGL). See the file `LICENSE` for details.

## Description

**WindowsPrivileges.pp** is a Free Pascal (FPC) unit for the Windows platform that lets you manage privileges and rights.

## Reference

This section documents the functions in the unit.

> IMPORTANT: The unit enables FPC's **UNICODESTRINGS** mode, so **string** = **UnicodeString** and **PChar** = **PWideChar**.

---

### GetPrivilegeName

Gets the properly cased name of the specified privilege or right.

#### Syntax

```
function GetPrivilegeName(const Name: string; out PrivilegeName: string): DWORD;
```

#### Parameters

`Name` - Specifies name of the privilege or right.

`PrivilegeName` - On successful return, contains the properly cased name of the privilege or right.

#### Return Value

The function returns 0 for success, or non-zero for failure.

---

### GetPrivilegeDisplayName

Gets the US English display name of the specified privilege or right.

#### Syntax

```
function GetPrivilegeDisplayName(const Name: string; out PrivilegeDisplayName: string): DWORD;
```

#### Parameters

`Name` - Specifies name of the privilege or right.

`PrivilegeName` - On successful return, contains the US English display name of the privilege or right.

#### Return Value

The function returns 0 for success, or non-zero for failure.

---

### EnumPrivileges

Gets an array of strings containing all privilege names.

#### Syntax

```
procedure EnumPrivileges(out Privileges: TStringArray);
```

#### Parameters

`Privileges` - An array of strings containing all privilege names.

---

### AddAccountPrivileges

Adds one or more privilges and/or rights to an account.

#### Syntax

```
function AddAccountPrivileges(const ComputerName, AccountName: string; var Privileges: TStringArray): DWORD;
```

#### Parameters

`ComputerName` - Specifies the name of the computer that contains the account. Specify an empty string to specify the current computer.

`AccountName` - Specifies the account name (user or group name).

`Privileges` - An array of strings containing the privileges and/or rights to add to the account.

#### Return Value

Returns 0 for success, or non-zero for failure.

---

### RemoveAccountPrivileges

Removes one or more privileges and/or rights from an account.

#### Syntax

```
function RemoveAccountPrivileges(const ComputerName, AccountName: string; var Privileges: TStringArray): DWORD;
```

#### Parameters

`ComputerName` - Specifies the name of the computer that contains the account. Specify an empty string to specify the current computer.

`AccountName` - Specifies the account name (user or group name).

`Privileges` - An array of strings containing the privileges and/or rights to remove from the account.

#### Return Value

Returns 0 for success, or non-zero for failure.

---

### EnumAccountPrivileges

Enumerates an account's privileges and rights.

#### Syntax

```
function EnumAccountPrivileges(const ComputerName, AccountName: string; out Privileges: TStringArray): DWORD;
```

#### Parameters

`ComputerName` - Specifies the name of the computer that contains the account. Specify an empty string to specify the current computer.

`AccountName` - Specifies the account name (user or group name).

`Privileges` - On successful return, contains an array of privileges and/or rights assigned to the account.

#### Return Value

Returns 0 for success, or non-zero for failure.

---
### TestAccountPrivileges

Tests whether an account has a list of privileges/rights directly assigned to it.

#### Syntax

```
function TestAccountPrivileges(const ComputerName, AccountName: string; var Privileges: TStringArray; out HasPrivileges: Boolean): DWORD;
```

#### Parameters

`ComputerName` - Specifies the name of the computer that contains the account. Specify an empty string to specify the current computer.

`AccountName` - Specifies the account name (user or group name).

`Privileges` - Specifies a string array of privileges to test.

`HasPrivileges` - On successful return, contains `true` if the specified account has all of the privileges and rights specified in the `Privileges` array directly assigned to it, or `false` otherwise.

#### Return Value

Returns 0 for success, or non-zero for failure.

---

### EnumPrivilegeAccounts

Gets a list of account names that have been directly assigned a particular privilege and/or right.

#### Syntax

```
function EnumPrivilegeAccounts(ComputerName, PrivilegeName: string; out Accounts: TStringArray): DWORD;
```

`ComputerName` - Specifies the name of the computer that contains the accounts. Specify an empty string to specify the current computer.

`PrivilegeName` - Specifies the privilege or right name.

`Accounts` - On successful return, contains a string array containing the account names (user or group names) that have the specified privilege or right directly assigned.

#### Return Value

Returns 0 for success, or non-zero for failure.

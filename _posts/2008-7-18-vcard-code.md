I mentioned in my last post that I was working on some vCard code.  I
figured I would post it here in case anybody is ever looking for a vCard
implementation in C\#.  This code generates a valid vCard, supports
multiple addresses and multiple phone numbers.  It does not even come
close to implementing the entire spec.  Since my target system was
Outlook, I saw no need to implement anything more than Outlook could
support.  My vCalendar implementation to follow.

Here it is:

      1: using System;\
     2: using System.Text;\
     3: using System.IO;\
     4: using System.Collections;\
     5:\
     6: namespace TT.Utility\
     7: {\
     8:     /// \<summary\>\
     9:     /// Summary description for Class1.\
    10:     /// \</summary\>\
    11:     public class VCard\
    12:     {\
    13:         private string \_formattedName;\
    14:         private string \_lastName;\
    15:         private string \_firstName;\
    16:         private string \_middleName;\
    17:         private string \_namePrefix;\
    18:         private string \_nameSuffix;\
    19:         private DateTime \_birthDate = DateTime.MinValue;\
    20:         private ArrayList \_addresses = new ArrayList();\
    21:         private ArrayList \_phoneNumber = new ArrayList();\
    22:         private ArrayList \_emailAddresses = new ArrayList();\
    23:         private string \_title;\
    24:         private string \_role;\
    25:         private string \_organization;\
    26:         \
    27:         public VCard()\
    28:         {\
    29:             //\
    30:             // TODO: Add constructor logic here\
    31:             //\
    32:         }\
    33:\
    34:         \#region Public Properties\
    35:         public string FormattedName\
    36:         {\
    37:             get{return \_formattedName;}\
    38:             set{\_formattedName = value;}\
    39:         }\
    40:         public string LastName\
    41:         {\
    42:             get{return \_lastName;}\
    43:             set{\_lastName = value;}\
    44:         }\
    45:         public string FirstName\
    46:         {\
    47:             get{return \_firstName;}\
    48:             set{\_firstName = value;}\
    49:         }\
    50:         public string MiddleName\
    51:         {\
    52:             get{return \_middleName;}\
    53:             set{\_middleName = value;}\
    54:         }\
    55:         public string NamePrefix\
    56:         {\
    57:             get{return \_namePrefix;}\
    58:             set{\_namePrefix = value;}\
    59:         }\
    60:         public string NameSuffix\
    61:         {\
    62:             get{return \_nameSuffix;}\
    63:             set{\_nameSuffix = value;}\
    64:         }\
    65:         public DateTime BirthDate\
    66:         {\
    67:             get{return \_birthDate;}\
    68:             set{\_birthDate = value;}\
    69:         }\
    70:         public ArrayList Addresses\
    71:         {\
    72:             get{return \_addresses;}\
    73:             set{\_addresses = value;}\
    74:         }\
    75:         public ArrayList PhoneNumber\
    76:         {\
    77:             get{return \_phoneNumber;}\
    78:             set{\_phoneNumber = value;}\
    79:         }\
    80:         public ArrayList EmailAddresses\
    81:         {\
    82:             get{return \_emailAddresses;}\
    83:             set{\_emailAddresses = value;}\
    84:         }\
    85:         public string Title\
    86:         {\
    87:             get{return \_title;}\
    88:             set{\_title = value;}\
    89:         }\
    90:         public string Role\
    91:         {\
    92:             get{return \_role;}\
    93:             set{\_role = value;}\
    94:         }\
    95:         public string Organization\
    96:         {\
    97:             get{return \_organization;}\
    98:             set{\_organization = value;}\
    99:         }\
   100:\
   101:         \#endregion\
   102:\
   103:         \#region Public Methods\
   104:\
   105:         public void Generate(string filePath, FileMode mode)\
   106:         {\
   107:             FileStream fs = new FileStream(filePath, mode);\
   108:\
   109:             Generate(fs);\
   110:         }\
   111:\
   112:         public void Generate(Stream outputStream)\
   113:         {\
   114:             StreamWriter sw = new StreamWriter(outputStream);\
   115:\
   116:             using (sw)\
   117:             {\
   118:                 sw.Write(this.ToString());\
   119:             }\
   120:         }\
   121:         \#endregion\
   122:\
   123:         public override string ToString()\
   124:         {\
   125:             StringBuilder sb = new StringBuilder();\
   126:\
   127:             //Start VCard\
   128:             sb.Append("BEGIN:VCARD\\r\\n");\
   129:\
   130:             //Add Formatted name\
   131:             if( \_formattedName != null )\
   132:             {\
   133:                 sb.Append("FN:" + \_formattedName + "\\r\\n");\
   134:             }\
   135:\
   136:             //Add the name\
   137:             sb.Append("N:" + \_lastName + ";");\
   138:             sb.Append(\_firstName + ";");\
   139:             sb.Append(\_middleName + ";");\
   140:             sb.Append(\_namePrefix + ";");\
   141:             sb.Append(\_nameSuffix + "\\r\\n");\
   142:\
   143:             //Add a birthday\
   144:             if( \_birthDate != DateTime.MinValue )\
   145:             {\
   146:                 sb.Append("BDAY:" +
\_birthDate.ToString("yyyyMMdd") + "\\r\\n");\
   147:             }\
   148:\
   149:             //Add Delivery Addresses\
   150:             foreach(DeliveryAddress da in \_addresses)\
   151:             {\
   152:                 sb.Append(da.ToString());\
   153:             }\
   154:\
   155:             //Add phone numbers\
   156:             foreach(TelephoneNumber phone in \_phoneNumber)\
   157:             {\
   158:                 sb.Append(phone.ToString());\
   159:             }\
   160:\
   161:             //Add email address\
   162:             foreach(string email in \_emailAddresses)\
   163:             {\
   164:                 sb.Append("EMAIL; INTERNET:" + email +
"\\r\\n");\
   165:             }\
   166:\
   167:             //Add Title\
   168:             sb.Append("TITLE:" + \_title + "\\r\\n");\
   169:\
   170:             //Business Category\
   171:             sb.Append("ROLE:" + \_role + "\\r\\n");\
   172:\
   173:             //Organization\
   174:             sb.Append("ORG:" + \_organization + "\\r\\n");\
   175:\
   176:             sb.Append("END:VCARD\\r\\n");\
   177:\
   178:             return sb.ToString();\
   179:         }\
   180:     }\
   181:\
   182:     public class DeliveryAddress\
   183:     {\
   184:         private string \_postOfficeAddress;\
   185:         private string \_extendedAddress;\
   186:         private string \_street;\
   187:         private string \_locality;\
   188:         private string \_region;\
   189:         private string \_postalCode;\
   190:         private string \_country;\
   191:\
   192:         public AddressType DeliveryAddressType;\
   193:         \
   194:         public DeliveryAddress()\
   195:         {\
   196:\
   197:         }\
   198:\
   199:         public string PostOfficeAddress\
   200:         {\
   201:             get{return \_postOfficeAddress;}\
   202:             set{\_postOfficeAddress = value;}\
   203:         }\
   204:         public string ExtendedAddress\
   205:         {\
   206:             get{return \_extendedAddress;}\
   207:             set{\_extendedAddress = value;}\
   208:         }\
   209:         public string Street\
   210:         {\
   211:             get{return \_street;}\
   212:             set{\_street = value;}\
   213:         }\
   214:         public string Locality\
   215:         {\
   216:             get{return \_locality;}\
   217:             set{\_locality = value;}\
   218:         }\
   219:         public string Region\
   220:         {\
   221:             get{return \_region;}\
   222:             set{\_region = value;}\
   223:         }\
   224:         public string PostalCode\
   225:         {\
   226:             get{return \_postalCode;}\
   227:             set{\_postalCode = value;}\
   228:         }\
   229:         public string Country\
   230:         {\
   231:             get{return \_country;}\
   232:             set{\_country = value;}\
   233:         }\
   234:\
   235:         public override string ToString()\
   236:         {\
   237:             StringBuilder sb = new StringBuilder();\
   238:             \
   239:             sb.Append("ADR;" + Enum.GetName(typeof(AddressType),
DeliveryAddressType) + ":");\
   240:             sb.Append(\_postOfficeAddress + ";");\
   241:             sb.Append(\_extendedAddress + ";");\
   242:             sb.Append(\_street + ";");\
   243:             sb.Append(\_locality + ";");\
   244:             sb.Append(\_region + ";");\
   245:             sb.Append(\_postalCode + ";");\
   246:             sb.Append(\_country + "\\r\\n");\
   247:\
   248:             return sb.ToString();\
   249:         }\
   250:\
   251:     }\
   252:\
   253:     public enum AddressType\
   254:     {\
   255:         DOM,\
   256:         INTL,\
   257:         POSTAL,\
   258:         PARCEL,\
   259:         HOME,\
   260:         WORK\
   261:     }\
   262:\
   263:     public class TelephoneNumber\
   264:     {\
   265:         private string \_phoneNumber;\
   266:\
   267:         public TelephoneNumberType PhoneNumberType;\
   268:         \
   269:         public TelephoneNumber()\
   270:         {\
   271:         }\
   272:\
   273:         public override string ToString()\
   274:         {\
   275:             StringBuilder sb = new StringBuilder();\
   276:\
   277:             sb.Append("TEL;" +
Enum.GetName(typeof(TelephoneNumberType), PhoneNumberType) + ":");\
   278:             sb.Append(\_phoneNumber + "\\r\\n");\
   279:\
   280:             return sb.ToString();\
   281:         }\
   282:\
   283:         public string PhoneNumber\
   284:         {\
   285:             get\
   286:             {\
   287:                 return \_phoneNumber;\
   288:             }\
   289:             set\
   290:             {\
   291:                 \_phoneNumber = value;\
   292:             }\
   293:         }\
   294:     }\
   295:\
   296:     public enum TelephoneNumberType\
   297:     {\
   298:         PREF,\
   299:         WORK,\
   300:         HOME,\
   301:         VOICE,\
   302:         FAX,\
   303:         MSG,\
   304:         CELL,\
   305:         PAGER,\
   306:         BBS,\
   307:         MODEM,\
   308:         CAR\
   309:     }\
   310: }\

 

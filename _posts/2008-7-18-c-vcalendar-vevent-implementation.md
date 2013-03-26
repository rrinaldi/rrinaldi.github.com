Here is a class that outputs a valid vCalendar string.  Again, not all
of the spec is implemented here since I was targeting Outlook. 
Everything that is here is all that Outlook supports (according to my
findings)

Hope it comes in handy:

    1: using System;\
     2: using System.Text;\
     3: using System.IO;\
     4: using System.Collections;\
     5:\
     6: namespace TT.Utility\
     7: {\
     8:     /// \<summary\>\
     9:     /// Summary description for vEvent.\
    10:     /// \</summary\>\
    11:     public class VEvent\
    12:     {\
    13:         private DateTime \_dateCreated = DateTime.Now;\
    14:         private DateTime \_endDateTime;\
    15:         private DateTime \_startDateTime;\
    16:         public ArrayList Categories = new ArrayList();\
    17:         public ClassificationType Classification =
ClassificationType.PUBLIC;\
    18:         \
    19:         private int \_priority = 0;\
    20:\
    21:         private string \_subject = "";\
    22:         private string \_description = "";\
    23:         \
    24:         \#region Public Constructors\
    25:         public VEvent()\
    26:         {\
    27:\
    28:         }\
    29:         \
    30:         public VEvent(string subject, string description,
DateTime startDateTime, DateTime endDateTime)\
    31:         {\
    32:             \_subject = subject;\
    33:             \_description = description;\
    34:             \_startDateTime = startDateTime;\
    35:             \_endDateTime = endDateTime;\
    36:         }\
    37:\
    38:         public VEvent(string subject, string description,
DateTime startDateTime, DateTime endDateTime, int priority)\
    39:         {\
    40:             \_subject = subject;\
    41:             \_description = description;\
    42:             \_priority = priority;\
    43:             \_startDateTime = startDateTime;\
    44:             \_endDateTime = endDateTime;\
    45:         }\
    46:\
    47:         public VEvent(string subject, string description,
DateTime startDateTime, TimeSpan meetingLength)\
    48:         {\
    49:             \_subject = subject;\
    50:             \_description = description;\
    51:             \_startDateTime = startDateTime;\
    52:             \_endDateTime = startDateTime.Add(meetingLength);\
    53:         }\
    54:\
    55:         public VEvent(string subject, string description,
DateTime startDateTime, TimeSpan meetingLength, int priority)\
    56:         {\
    57:             \_subject = subject;\
    58:             \_description = description;\
    59:             \_priority = priority;\
    60:             \_startDateTime = startDateTime;\
    61:             \_endDateTime = startDateTime.Add(meetingLength);\
    62:         }\
    63:\
    64:         \#endregion\
    65:         \
    66:         public void Generate(string filePath, FileMode mode)\
    67:         {\
    68:             FileStream fs = new FileStream(filePath, mode);\
    69:\
    70:             Generate(fs);\
    71:         }\
    72:\
    73:         public void Generate(Stream outputStream)\
    74:         {\
    75:             StreamWriter sw = new StreamWriter(outputStream);\
    76:\
    77:             using (sw)\
    78:             {\
    79:                 sw.Write(this.ToString());\
    80:             }\
    81:         }\
    82:\
    83:         public override string ToString()\
    84:         {\
    85:             StringBuilder sb = new StringBuilder();\
    86:             \
    87:             //Start the event\
    88:             sb.Append("BEGIN:VCALENDAR\\r\\n");\
    89:             sb.Append("VERSION:1.0\\r\\n");\
    90:             sb.Append("BEGIN:VEVENT\\r\\n");\
    91:             \
    92:             //Add the date created\
    93:             sb.Append("DCREATED: " +
\_dateCreated.ToUniversalTime().ToString("yyyyMMddTHHmmssZ") +
"\\r\\n");\
    94:             \
    95:             sb.Append("DTSTART: " +
\_startDateTime.ToUniversalTime().ToString("yyyyMMddTHHmmssZ") +
"\\r\\n");\
    96:             sb.Append("DTEND: " +
\_endDateTime.ToUniversalTime().ToString("yyyyMMddTHHmmssZ") +
"\\r\\n");\
    97:\
    98:             sb.Append("PRIORITY: " + \_priority + "\\r\\n");\
    99:\
   100:             sb.Append("SUMMARY: " + \_subject + "\\r\\n");\
   101:             sb.Append("DESCRIPTION: " + \_description +
"\\r\\n");\
   102:\
   103:             if( Categories.Count != 0 )\
   104:             {\
   105:                 sb.Append("CATEGORIES: ");\
   106:                 foreach(string category in Categories)\
   107:                 {\
   108:                     sb.Append( category + ";" );\
   109:                 }\
   110:                 sb.Append( "\\r\\n" );\
   111:             }\
   112:\
   113:             sb.Append("CLASS:" +
Enum.GetName(typeof(ClassificationType), Classification) + "\\r\\n" );\
   114:\
   115:             //End the event\
   116:             sb.Append("END:VEVENT\\r\\n");\
   117:             sb.Append("END:VCALENDAR\\r\\n");\
   118:\
   119:             return sb.ToString();\
   120:         }\
   121:         \
   122:         /// \<summary\>\
   123:         /// DateTime that the vEvent was created. Not required.
Defaults to current date and time.\
   124:         /// \</summary\>\
   125:         public DateTime DateCreated\
   126:         {\
   127:             get\
   128:             {\
   129:                 return \_dateCreated;\
   130:             }\
   131:\
   132:             set\
   133:             {\
   134:                 \_dateCreated = value;\
   135:             }\
   136:         }\
   137:\
   138:         /// \<summary\>\
   139:         /// DateTime that the vEvent will be done.\
   140:         /// \</summary\>\
   141:         public DateTime EndDateTime\
   142:         {\
   143:             get\
   144:             {\
   145:                 return \_endDateTime;\
   146:             }\
   147:\
   148:             set\
   149:             {\
   150:                 \_endDateTime = value;\
   151:             }\
   152:         }\
   153:\
   154:         /// \<summary\>\
   155:         /// DateTime that the vEvent will start.\
   156:         /// \</summary\>\
   157:         public DateTime StartDateTime\
   158:         {\
   159:             get\
   160:             {\
   161:                 return \_startDateTime;\
   162:             }\
   163:\
   164:             set\
   165:             {\
   166:                 \_startDateTime = value;\
   167:             }\
   168:         }\
   169:\
   170:         /// \<summary\>\
   171:         /// Any valid Int32. 0 is undefined. 1 is High Priority.
-1 is Low Priority. Defaults to 0.\
   172:         /// \</summary\>\
   173:         public int Priority\
   174:         {\
   175:             get\
   176:             {\
   177:                 return \_priority;\
   178:             }\
   179:\
   180:             set\
   181:             {\
   182:                 \_priority = value;\
   183:             }\
   184:         }\
   185:\
   186:         /// \<summary\>\
   187:         /// Subject of the vEvent\
   188:         /// \</summary\>\
   189:         public string Subject\
   190:         {\
   191:             get\
   192:             {\
   193:                 return \_subject;\
   194:             }\
   195:\
   196:             set\
   197:             {\
   198:                 \_subject = value;\
   199:             }\
   200:         }\
   201:\
   202:         /// \<summary\>\
   203:         /// Description of the vEvent\
   204:         /// \</summary\>\
   205:         public string Description\
   206:         {\
   207:             get\
   208:             {\
   209:                 return \_description;\
   210:             }\
   211:\
   212:             set\
   213:             {\
   214:                 \_description = value;\
   215:             }\
   216:         }\
   217:     }\
   218:\
   219:     public enum ClassificationType\
   220:     {\
   221:         PUBLIC,\
   222:         PRIVATE,\
   223:         CONFIDENTIAL\
   224:     }\
   225: }\


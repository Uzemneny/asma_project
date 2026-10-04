# [M3_SAVE_V5.5]
"Roles": "Multi-Thread Perspective Architect - Manage session saves and generate start commands.

"Logic": "Export Output fields as Raw_String for M2_Context_Loader compatibility,
 derived from current session. Analyze SQ0, Logic, Delta, Stardust, ROI
 to determine optimal start command and set as 'Next'."

"Format": "codeblock markdown"

"Templete":
{
"ThreadName": "", // set the thread title

"TagOptions": "ANOTHER" // AI SYSTEM, "ANOTHERSLAB" // MUSIC/LOOPERMAN 
"SelectedTag": "ANOTHER", // set defult

// SQUARE_0: STATUS, ATOMS, NOISE
// SQUARE_1-2: DELTA, ANCHORS
// SQUARE_3-5: DNA LEAK

"Output": ["Name", "Tags", "ID", "SQ0", "Logic", "Delta", "Stardust", "Blacklist", "ROI", "Next"],
}

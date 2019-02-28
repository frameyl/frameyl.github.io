TF_CPP_MIN_LOG_LEVEL - which has 3 or 4 basic levels - low numbers = more messages.
0 outputs Information, Warning, Error, and Fatals (default)
1 outputs Warning, and above
2 outputs Errors and above.
etc... I didn't check edge cases
TF_CPP_MIN_VLOG_LEVEL - which causes very very many extra Information errors - really for debugging only - low numbers = less messages.
3 Outputs lots and lots of stuff
2 Outputs less
1 Outputs even less
0 Outputs nothing extra (default)

https://blog.qikqiak.com/post/update-kubernetes-dashboard-more-secure/
https://jimmysong.io/kubernetes-handbook/guide/auth-with-kubeconfig-or-token.html

kubectl -n kube-system get secret|grep admin-token
kubectl -n kube-system get secret admin-token-n8dsf -o jsonpath={.data.token}|base64 -d

`eyJhbGciOiJSUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJrdWJlcm5ldGVzL3NlcnZpY2VhY2NvdW50Iiwia3ViZXJuZXRlcy5pby9zZXJ2aWNlYWNjb3VudC9uYW1lc3BhY2UiOiJrdWJlLXN5c3RlbSIsImt1YmVybmV0ZXMuaW8vc2VydmljZWFjY291bnQvc2VjcmV0Lm5hbWUiOiJhZG1pbi10b2tlbi14dzJjMiIsImt1YmVybmV0ZXMuaW8vc2VydmljZWFjY291bnQvc2VydmljZS1hY2NvdW50Lm5hbWUiOiJhZG1pbiIsImt1YmVybmV0ZXMuaW8vc2VydmljZWFjY291bnQvc2VydmljZS1hY2NvdW50LnVpZCI6IjM5MzA3Njg3LWU5ODQtMTFlOC1hZTZmLWY0OGUzOGI2MmZlNSIsInN1YiI6InN5c3RlbTpzZXJ2aWNlYWNjb3VudDprdWJlLXN5c3RlbTphZG1pbiJ9.lP8n7DISfHiJ2pGAqKqt7M5MJjYtL0da7DxuDRtO1KuCGAAq82BsWMJznkagq0yaQaTBqF227DOeFhV2Etl7v54JDk1ZbeMaWs44QWswLqCHoZXt_BGR2gk7wjZo4qGaS7pAXzoNsjOFa7wmpHLdc0cx8kTn9nml9FSjTp7TevyTXvHYTMtegI-ZLZUAVTIrt9tQEAqYcniHZtVxrfyUS-__zti12xpezrN21pBmTRgXMV0CViE-kmyBnk6Zl4AtpBoMeP2r1t_gyrNGtoWoshfXBatx-gPDG1HqtgCI-mQ1etFrOX4E4xNgK4pPZtggBT5ppmjU6mrOIxEuPuVbag`

kubectl get secret | grep default-token
kubectl get secret default-token-bjtt5 -o jsonpath={.data.token}|base64 -d

`eyJhbGciOiJSUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJrdWJlcm5ldGVzL3NlcnZpY2VhY2NvdW50Iiwia3ViZXJuZXRlcy5pby9zZXJ2aWNlYWNjb3VudC9uYW1lc3BhY2UiOiJkZWZhdWx0Iiwia3ViZXJuZXRlcy5pby9zZXJ2aWNlYWNjb3VudC9zZWNyZXQubmFtZSI6ImRlZmF1bHQtdG9rZW4tYmp0dDUiLCJrdWJlcm5ldGVzLmlvL3NlcnZpY2VhY2NvdW50L3NlcnZpY2UtYWNjb3VudC5uYW1lIjoiZGVmYXVsdCIsImt1YmVybmV0ZXMuaW8vc2VydmljZWFjY291bnQvc2VydmljZS1hY2NvdW50LnVpZCI6ImVlMTNhZTUwLTU0MjYtMTFlOC04N2MyLWY0OGUzOGI2MmZlNSIsInN1YiI6InN5c3RlbTpzZXJ2aWNlYWNjb3VudDpkZWZhdWx0OmRlZmF1bHQifQ.Q9d7B0f0IM1i3JzcQChM6enKNfoIGqHII6Lp0jEvD6oFRdR8tBY1sh8R84zTMOejHR8Y6hXOG3Y5aK-2ojPmS-Cu12xBXHf4_oelCZYseZ8JAIq062EfQ4qT97dbhiMyW_R44fFM6GUFqqu2wmNhGpnZhjsZGa2mkexZEa8rnvqVM_J_E4UF35kRfOQF7tdTGjYxPjaJsn2Nxcb9AXBCZcXs7OMuaKff9V6ZVqW67WctM6H3Pe6KNgRycDPCPb28DJ5AouGPigkkUWuXsPKz7zoWe2sbBkDctMtvojPAL15JSQww52XiBOSPTdWCBv4_fbAKLptcf7sfhqLuOUDY-g`


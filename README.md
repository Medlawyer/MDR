# MDR-platform
import React, { useState } from 'react';
import { Card, CardHeader, CardContent } from '@/components/ui/card';
import { Tabs, TabsContent, TabsList, TabsTrigger } from '@/components/ui/tabs';
import { Button } from '@/components/ui/button';
import { 
  Hospital, FileText, BookOpen, 
  ClipboardCheck, Certificate, 
  Download, Plus 
} from 'lucide-react';

const RegistrationSystem = () => {
  const [selectedModule, setSelectedModule] = useState('podmiot');

  const documentTypes = {
    podmiotLeczniczy: [
      "Wniosek o wpis do rejestru podmiotów wykonujących działalność leczniczą",
      "Regulamin organizacyjny",
      "Dokumentacja pomieszczeń (wymogi sanitarne)",
      "Umowy z personelem medycznym",
      "Polisa OC",
      "Procedury MDR dla wyrobów medycznych"
    ],
    
    centrumKsztalcenia: [
      "Wniosek o wpis do ewidencji szkół i placówek niepublicznych",
      "Statut placówki",
      "Program kształcenia",
      "Dokumentacja kadry dydaktycznej",
      "Regulamin placówki",
      "Wzory świadectw i certyfikatów"
    ],

    procedury: [
      "Procedura zarządzania wyrobami medycznymi",
      "Procedura zgłaszania incydentów medycznych",
      "Procedura nadzoru nad dokumentacją",
      "Procedura identyfikacji i monitorowania wyrobów",
      "Procedura szkoleń personelu",
      "Procedura kontroli jakości"
    ]
  };

  return (
    <div className="min-h-screen bg-gray-50 p-4">
      <div className="max-w-7xl mx-auto">
        <div className="mb-8">
          <h1 className="text-3xl font-bold text-gray-900">System Rejestracji i Zarządzania</h1>
          <p className="text-gray-600">Kompleksowe zarządzanie dokumentacją i procedurami</p>
        </div>

        <Tabs value={selectedModule} onValueChange={setSelectedModule}>
          <TabsList className="grid grid-cols-3 gap-4 mb-8">
            <TabsTrigger value="podmiot">
              <Hospital className="w-5 h-5 mr-2" />
              Podmiot Leczniczy
            </TabsTrigger>
            <TabsTrigger value="centrum">
              <BookOpen className="w-5 h-5 mr-2" />
              Centrum Kształcenia
            </TabsTrigger>
            <TabsTrigger value="procedury">
              <ClipboardCheck className="w-5 h-5 mr-2" />
              Procedury MDR
            </TabsTrigger>
          </TabsList>

          {/* Podmiot Leczniczy */}
          <TabsContent value="podmiot">
            <div className="grid grid-cols-1 md:grid-cols-2 gap-6">
              <Card>
                <CardHeader>
                  <h3 className="text-xl font-semibold">Rejestracja Podmiotu Leczniczego</h3>
                  <p className="text-gray-600">Dokumenty wymagane do rejestracji</p>
                </CardHeader>
                <CardContent>
                  <div className="space-y-4">
                    {documentTypes.podmiotLeczniczy.map((doc, index) => (
                      <div key={index} className="flex items-center justify-between p-3 bg-gray-50 rounded-lg">
                        <span className="flex-1">{doc}</span>
                        <div className="flex gap-2">
                          <Button variant="outline" size="sm">
                            <Plus className="w-4 h-4 mr-1" />
                            Utwórz
                          </Button>
                          <Button variant="outline" size="sm">
                            <Download className="w-4 h-4 mr-1" />
                            Pobierz
                          </Button>
                        </div>
                      </div>
                    ))}
                  </div>
                </CardContent>
              </Card>

              <Card>
                <CardHeader>
                  <h3 className="text-xl font-semibold">Status Rejestracji</h3>
                  <p className="text-gray-600">Postęp procesu rejestracyjnego</p>
                </CardHeader>
                <CardContent>
                  <div className="space-y-4">
                    <div className="w-full bg-gray-200 rounded-full h-2.5">
                      <div className="bg-blue-600 h-2.5 rounded-full" style={{ width: '45%' }}></div>
                    </div>
                    <div className="grid grid-cols-2 gap-4">
                      <Button className="w-full">
                        <FileText className="w-4 h-4 mr-2" />
                        Lista kontrolna
                      </Button>
                      <Button variant="outline" className="w-full">
                        <Certificate className="w-4 h-4 mr-2" />
                        Status prawny
                      </Button>
                    </div>
                  </div>
                </CardContent>
              </Card>
            </div>
          </TabsContent>

          {/* Centrum Kształcenia */}
          <TabsContent value="centrum">
            <div className="grid grid-cols-1 md:grid-cols-2 gap-6">
              <Card>
                <CardHeader>
                  <h3 className="text-xl font-semibold">Rejestracja Centrum Kształcenia</h3>
                  <p className="text-gray-600">Wymagana dokumentacja</p>
                </CardHeader>
                <CardContent>
                  <div className="space-y-4">
                    {documentTypes.centrumKsztalcenia.map((doc, index) => (
                      <div key={index} className="flex items-center justify-between p-3 bg-gray-50 rounded-lg">
                        <span className="flex-1">{doc}</span>
                        <div className="flex gap-2">
                          <Button variant="outline" size="sm">
                            <Plus className="w-4 h-4 mr-1" />
                            Utwórz
                          </Button>
                          <Button variant="outline" size="sm">
                            <Download className="w-4 h-4 mr-1" />
                            Pobierz
                          </Button>
                        </div>
                      </div>
                    ))}
                  </div>
                </CardContent>
              </Card>

              <Card>
                <CardHeader>
                  <h3 className="text-xl font-semibold">Zarządzanie Szkoleniami</h3>
                  <p className="text-gray-600">System szkoleń i certyfikacji</p>
                </CardHeader>
                <CardContent>
                  <div className="space-y-4">
                    <Button className="w-full">
                      <Plus className="w-4 h-4 mr-2" />
                      Nowy program szkoleniowy
                    </Button>
                    <Button variant="outline" className="w-full">
                      <Certificate className="w-4 h-4 mr-2" />
                      Generuj certyfikaty
                    </Button>
                  </div>
                </CardContent>
              </Card>
            </div>
          </TabsContent>

          {/* Procedury MDR */}
          <TabsContent value="procedury">
            <div className="grid grid-cols-1 md:grid-cols-2 gap-6">
              <Card>
                <CardHeader>
                  <h3 className="text-xl font-semibold">Procedury MDR</h3>
                  <p className="text-gray-600">Zgodne z rozporządzeniem UE 2017/745</p>
                </CardHeader>
                <CardContent>
                  <div className="space-y-4">
                    {documentTypes.procedury.map((doc, index) => (
                      <div key={index} className="flex items-center justify-between p-3 bg-gray-50 rounded-lg">
                        <span className="flex-1">{doc}</span>
                        <div className="flex gap-2">
                          <Button variant="outline" size="sm">
                            <Plus className="w-4 h-4 mr-1" />
                            Utwórz
                          </Button>
                          <Button variant="outline" size="sm">
                            <Download className="w-4 h-4 mr-1" />
                            Pobierz
                          </Button>
                        </div>
                      </div>
                    ))}
                  </div>
                </CardContent>
              </Card>

              <Card>
                <CardHeader>
                  <h3 className="text-xl font-semibold">Monitoring i Raporty</h3>
                  <p className="text-gray-600">System nadzoru nad wyrobami</p>
                </CardHeader>
                <CardContent>
                  <div className="space-y-4">
                    <Button className="w-full">
                      <Plus className="w-4 h-4 mr-2" />
                      Nowy raport zgodności
                    </Button>
                    <Button variant="outline" className="w-full">
                      <ClipboardCheck className="w-4 h-4 mr-2" />
                      Historia audytów
                    </Button>
                  </div>
                </CardContent>
              </Card>
            </div>
          </TabsContent>
        </Tabs>
      </div>
    </div>
  );
};

export default RegistrationSystem;
# Class Relationships: Association and Multiplicity 
## Previous Work 
[Part I - Classes and Objects](classObjectUML.md) 
[Part II - Class Attributes and Methods](classAttributesMethods.md) 

## Existing Class 
Class: Danza Serenata
Description: A school club/organization that combines the three disciplines (Dance Troupe, Harmonia, Rondalla)

## New Related Class 
Class: Performers
Description: The students who are members of the Danza Serenata organization. 

## Association 
Relationship: Danza Serenata contains Performers
Explanation: The performers are individuals who apply the 3 disciplines under the Danza Serenata. 

## Multiplicity
Multiplicity: One-to-many
Explanation: A single organization may contain zero or more performers. Every performer is directed to only to the Danza Serenata

## UML Class Relationship Diagram 
![Class Relationship Diagram](images/classRelationshipDiagram.png) 

## Python Implementation 
# classRelationships.py

class Performer:
    def __init__(self, name: str, role: str, talent_skill: str):
            self.name = name
                    self.role = role
                            self.talent_skill = talent_skill

                                def display_profile(self):
                                        print(f"  - Name: {self.name} | Role: {self.role} | Skill: {self.talent_skill}")


                                        class DanzaSerenata:
                                            def __init__(self, adviser: str, total_members: int, instruments: bool, voice: bool, dance_ability: bool):
                                                    self.adviser = adviser
                                                            self.total_members = total_members
                                                                    self._instruments = instruments
                                                                            self._voice = voice
                                                                                    self._dance_ability = dance_ability
                                                                                            self._performers = []  

                                                                                                def dance(self):
                                                                                                        if self._dance_ability:
                                                                                                                    print(f"The Danza Serenata dance troupe is performing a choreography!")

                                                                                                                        def sing(self):
                                                                                                                                if self._voice:
                                                                                                                                            print(f"Harmonia group is performing vocal harmonies!")

                                                                                                                                                def play_instruments(self):
                                                                                                                                                        if self._instruments:
                                                                                                                                                                    print(f"Rondalla group is playing musical instruments!")

                                                                                                                                                                        def add_performer(self, performer_obj: Performer):
                                                                                                                                                                                self._performers.append(performer_obj)
                                                                                                                                                                                        self.total_members = len(self._performers)

                                                                                                                                                                                            def list_performers(self):
                                                                                                                                                                                                    if not self._performers:
                                                                                                                                                                                                                print("No performers registered yet.")
                                                                                                                                                                                                                        else:
                                                                                                                                                                                                                                    for performer in self._performers:
                                                                                                                                                                                                                                                    performer.display_profile()


                                                                                                                                                                                                                                                    ## Test Run 
                                                                                                                                                                                                                                                    ![Relationship Test Run](images/relationshipTestRun.png) 
                                                                                                                                                                                                                                                    ## Object Relationship Diagram 
                                                                                                                                                                                                                                                    ![Object Relationship Diagram](images/objectRelationshipDiagram.png) 

                                                                                                                                                                                                                                                    ## Analysis 

                                                                                                                                                                                                                                                    ###What is the association between your two classes?
                                                                                                                                                                                                                                                    The link between Danza Serenata and Performer is basically a simple "has-a" setup where our group holds the actual student performers. Danza Serenata acts like the main container or group that holds onto all the performer profiles. Then, each Performer object is just a real student in the group who brings in their own skill, like dancing or playing an instrument.

                                                                                                                                                                                                                                                    ###What multiplicity did you choose and why?
                                                                                                                                                                                                                                                    One-to-Many multiplicity because one Danza Serenata group can have zero performers at first or a bunch of them once people join. It makes sense because a real school club needs to hold a lot of members to actually perform. On the other side, each individual performer is just tied to this one specific Danza Serenata group.

                                                                                                                                                                                                                                                    ###How did you implement the relationship in Python?
                                                                                                                                                                                                                                                    To build this in Python, I created an empty list called self._performers inside the init constructor of Danza Serenata. Then I made a small function called add_performer() that just appends any new Performer object straigt into that list. This lets the main group keep track of everyone who joins without breaking anything.

                                                                                                                                                                                                                                                    ###Why did you store an object reference instead of copying its data?
                                                                                                                                                                                                                                                    I stored the actual object reference so I wouldnt have to copy-paste data everywhere and make a mess. For example, if a performer changes their talent skill later on, Danza Serenata automatically sees the updated info because its pointing right at the original object. If I just copied text strings over, I would have to manually update them in two different places, which easily leads to mistakes.
o
                                                                                                                                                                                                                                                    ### If your relationship uses many, why is a list appropriate?
                                                                                                                                                                                                                                                    Using a Python list works super well for a "many" setup because it can grow or shrink whenever we want. I can easily add new members on the fly using append() as more performers join. Plus, it makes it super easy to loop through everyone with a simple for loop whenever I need to print out all the performer details at once.



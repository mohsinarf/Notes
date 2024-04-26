## I2C vs SPI

| Feature            | I2C                                   | SPI                                             |
|--------------------|---------------------------------------|-------------------------------------------------|
| Number of Pins     | 2 (SCL, SDA)                          | Minimum 4 (SCK, MOSI, MISO, SS per device)     |
| Topology           | Multi-master, addressing              | Master-slave, no addressing                    |
| Data Transfer Speed| Slower, half-duplex                   | Faster, full-duplex                            |
| Complexity         | Easier, fewer hardware pins           | More complex, more hardware resources          |
| Buffering          | Less buffering                        | More buffering                                 |
| Power Consumption  | Generally lower                       | May be higher                                  |
| Applications       | Low-speed communication               | High-speed communication                       |
